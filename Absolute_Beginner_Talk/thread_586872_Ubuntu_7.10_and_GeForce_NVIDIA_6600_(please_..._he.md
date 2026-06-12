---
title: "Ubuntu 7.10 and GeForce NVIDIA 6600 (please ... help !!!!)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by joakim2008 on 2007-10-22
I used ENVY to install the last Drivers of the GeForce 6600 but still the X Server won't start.

I don't know what to do ... (noob at linux)

This is my failsafeXServer file

```
#!/bin/bash

# $Id:$
#
# This provides a stripped down 'failsafe' mode for situations
# where X is failing to start up.

# Author: Bryce W. Harrington <bryce@canonical.com>

# Copyright 2007 Canonical, Ltd
#
# This is free software; you may redistribute it and/or modify
# it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2,
# or (at your option) any later version.
#
# This is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License with
# the Debian operating system, in /usr/share/common-licenses/GPL;  if
# not, write to the Free Software Foundation, Inc., 59 Temple Place,
# Suite 330, Boston, MA 02111-1307 USA

xorg_conf_failsafe=${BPX_XORG_CONF_FAILSAFE:-"/etc/X11/xorg.conf.failsafe"}
xorg_conf=${BPX_XORG_CONF:-"/etc/X11/xorg.conf"}

run_dexconf=${BPX_RUN_DEXCONF:-"yes"}

# TODO:  This should be set to "vga", however I have been unable to
#        succeed in getting the vga driver running in anything over
#        320x200, which is unusable.  So fallback is disabled for now.
#fallback_driver="vga"
fallback_driver=${BPX_FALLBACK_DRIVER:-"vesa"}

client=${BPX_CLIENT:-"/etc/gdm/failsafeXinit"}
clientargs=${BPX_CLIENTARGS:-$xorg_conf_failsafe}
blacklist=${BPX_BLACKLIST:-"/etc/gdm/failsafeBlacklist"}
main_driver=${BPX_DRIVER:-"vesa"}
checkduration=${BPX_CHECK_DURATION:-30}
failsafe_log=${BPX_LOG:-"/var/log/gdm/failsafe.log"}

server=${BPX_SERVER:-/usr/bin/X}
serverargs=${BPX_SERVERARGS:-"$*"}
if [ -z $serverargs ]; then
    # Use :10 to avoid overwriting the (failed) Xorg.0.log
    serverargs=":10"
fi
serverargs="${serverargs} -br -once -config $xorg_conf_failsafe"
   # -br:      Black background
   # -once:    Terminate server after one session
   # -config:  Specify location of xorg.conf file to use
   #           Note: Only root can specify absolute paths

warn() {
    echo "Warning:  $1" 1>&2
}

is_installed() {
    prog=$1
    need=$2
    /usr/bin/which $prog > /dev/null 2>&1
    err=$?
    if [ ! $err = 0 ]; then
	warn "Could not $need because $prog is not installed ($err)"
	return $err
    fi
    return 0
}

# Tests if the given pciids are in numerical order from least to greatest
# (e.g., $a <= $b <= $c <= ...)
pciids_in_order() {
    lastid=0
    for pciid in $* ; do
        # Strip embedded : and convert hex to dec
        id=$((0x${pciid/:/}))
        if [ $id -lt $lastid ]; then
            return 1
        fi
        lastid=$id
    done
    return 0
}

get_edid() {
    # Retrieve EDID (if get-edid is installed)
    is_installed get-edid "retrieve EDID" || return 1

    # Discard stderr, which is text data about the card
    get-edid 2>/dev/null
}

get_pciids() {
    # Retrieve PCI IDs from discover
    is_installed discover "retreive PCI IDs" || return 1

    discover --enable-all video --format="%i\n"
}

get_driver() {
    EDID=$(get_edid)
    PCIIDS=$(get_pciids)

    if [ "x$EDID" = "x" ]; then
	echo $fallback_driver
	return 1
    elif [ "x$PCIIDS" = "x" ]; then
	echo $fallback_driver
	return 2
    fi

    # TODO:  What if we have multiple pciids?  Assume first for now.
    pciid=$(echo $PCIIDS | head -n 1)

    EDID_MD5=$(echo $EDID | md5sum | head -n1 | cut -d" " -f1)
    matches=$(egrep "^$EDID_MD5|^ANY" $blacklist)
    found="no"
    for line in "$matches"; do
	line=$(echo $line | sed -e "s/ \+/ /")
	range=$(echo $line | cut -d' ' -f 2)
	driver=$(echo $line | cut -d' ' -f 3)
	pciid1=$(echo $range | cut -d- -f 1)
	pciid2=$(echo $range | cut -d- -f 2)

	if [ "x$pciid1" = "x" ]; then
            continue
	elif [ "x$pciid1" = "xANY" ]; then
	    found="yes"
	    break
	elif [ "$pciid1" = "$pciid" ]; then
	    found="yes"
	    break
	elif [ "x$pciid2" = "x" ]; then
            continue
	elif pciids_in_order $pciid1 $pciid $pciid2 ; then
	    found="yes"
	    break
	fi
    done

    if [ $found = "no" ]; then
	echo $main_driver

    else
	# No driver was specified - assume vga
	if [ "x$driver" = "x" ]; then
	    warn "System is blacklisted, but no driver specified; assuming fallback"
	    driver=$fallback_driver
	fi

	echo $driver
    fi

    return 0
}

# Check if we've already attempted a failsafe session without success
if [ -e "$failsafe_log" ]; then
    cur_time=$(date +"%s")
    last_run=$(tail -n 1 $failsafe_log | cut -d' ' -f1)
    time_diff=$(expr $cur_time - $last_run)
    if [ $time_diff -lt $checkduration ]; then
        warn "Failsafe mode was already attempted within $checkduration seconds."
        warn "Falling back to gdm to report the issue."
        exit 1
    fi
fi

# When failsafe mode is activated, check the blacklist for systems we
# know do not support VESA 800x600/256
#      Use EDID + PCI IDs as key to lookup (Can get PCI IDs from discover)
#      If the display does not give EDID info, then use VGA 640x480/16 mode
#      If a matching entry is found, then use VGA 640x480/16 mode
driver=$(get_driver)

if [ "x${run_dexconf}" = "xyes" ]; then
    # Generate an appropriate xorg.conf
    /etc/gdm/failsafeDexconf $driver $xorg_conf_failsafe
    if [ ! -s $xorg_conf_failsafe ]; then
        warn "Could not generate $xorg_conf_failsafe for $driver driver"
        exit 1
    fi
elif [ ! -s $xorg_conf_failsafe ]; then
    warn "Requested to use $xorg_conf_failsafe for $driver driver, but it does not exist"
    exit 1
fi

md5xorg=$(md5sum $xorg_conf)
date +"%s $md5xorg" >> $failsafe_log
if [ $? -ne 0 ]; then
    warn "Cannot write to $failsafe_log"
fi

# TODO:  Start up the failsafe X session using their regular user account

if pidof /usr/sbin/gdm ; then
    clientargs="${clientargs} with-gdm"
fi

echo "xinit $client $clientargs -- $server $serverargs"
xinit $client $clientargs -- $server $serverargs &

sleep 3

# Stop gdm if it's running, otherwise it will attempt to manage the display
# out from under us
if pidof /usr/sbin/gdm ; then
    exec kill -STOP $PPID
fi

# This seems to cause gdm to attempt to start a new x session
#exec kill -USR1 `cat /var/run/gdm.pid`
```

and this is my xorg.conf file

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"S3 Inc. 86c764/765 [Trio32/64/64V+]"
	Driver		"nvidia"
	BusID		"PCI:0:8:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"&#915;&#949;&#957;&#953;&#954;&#942; &#927;&#952;&#972;&#957;&#951;"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86c764/765 [Trio32/64/64V+]"
	Monitor		"&#915;&#949;&#957;&#953;&#954;&#942; &#927;&#952;&#972;&#957;&#951;"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```


please help me !!! i am desperate asking for a solution ! my monitor is DELL E172FP

all went right with ENVY but UBUNTU still can identify my card and monitor... 


thanx in advance

---

### Post by dexter on 2007-10-22
Why don't you use the restricted driver manager ?

---

### Post by skinja on 2007-10-22
Looks like ENVY made it.
First, from command line:
sudo dpkg-reconfigure xserver-xorg
then uninstall ENVY.

---

### Post by Perfect Storm on 2007-10-22
> Identifier	"S3 Inc. 86c764/765 [Trio32/64/64V+]"

That aren't a nvidia card? That might be the problem.

---

### Post by skinja on 2007-10-22
:confused:GeForce NVIDIA 6600

---

### Post by joakim2008 on 2007-10-22
Thanx for taking care of my problem but please (with all the respect) be more specific... ( i can't get it all with one word).


I saw that my card wasn't S3... and tried to change it... but with no hope.


Please be specific with help (what to write and under what environment [gde or tty1])


thanx again !

---

### Post by dynamethod on 2007-10-22
my 2 cents but, try COMPLETELY removing the driver you installed with Envy, then try install your driver, dont try reinstall over the already installed driver

---

### Post by joakim2008 on 2007-10-22
sorry again. how can i COMPLETELY Uninstall the Driver I installed? Will I use ENVY again? and then how can I re-install my driver ?

---

### Post by alb@nian on 2007-10-22
Did you enable the nvidia drivers in the restricted driver panel. 
```

System/adminnistration/restricted driver manager
```

---

### Post by dynamethod on 2007-10-22
> **joakim2008 said:**
> sorry again. how can i COMPLETELY Uninstall the Driver I installed? Will I use ENVY again? and then how can I re-install my driver ?

yeah just reinstall Envy if yourve uninstalled it, then choose the option to remove your NVIDIA driver, once your've done that, try reinstalling again with Envy

---

### Post by joakim2008 on 2007-10-22
I went to restricted drivers but said that my hardware doesn't need any restricted drivers.... !!!!!!! what is goin' on ?

---

### Post by mikewhatever on 2007-10-22
You should let envy reconfigure xserver, not only download and install the driver, also, any idea what's this 
> Monitor		"&#915;&#949;&#957;&#953;&#954;&#942; &#927;&#952;&#972;&#957;&#951;"

---

### Post by joakim2008 on 2007-10-22
> **dynamethod said:**
> yeah just reinstall Envy if yourve uninstalled it, then choose the option to remove your NVIDIA driver, once your've done that, try reinstalling again with Envy

i uninstalled with ENVY my previous drivers before using ENVY to install the new at the first time.... shoud i do that once more ?

---

### Post by joakim2008 on 2007-10-22
> **mikewhatever said:**
> You should let envy reconfigure xserver, not only download and install the driver.

i didn't prevent ENVY from reconfiguring xserver. I uninstalled the drivers i had with ENVY option, then i installed the NVIDIA Drivers from ENVY. It didn't say any ware about letting or not ENVY to reconfigure xserver... should i do that after the install and if i have to how ?

---

### Post by joakim2008 on 2007-10-22
> **mikewhatever said:**
> Monitor "&#915;&#949;&#957;&#953;&#954;&#942; &#927;&#952;&#972;&#957;&#951;"

i use greek ubuntu so that is the greek translation for "General Monitor"

---

### Post by dynamethod on 2007-10-22
> **joakim2008 said:**
> i uninstalled with ENVY my previous drivers before using ENVY to install the new at the first time.... shoud i do that once more ?

yeah give it another try, but after you uninstall the driver with Envy, try a reboot and THEN install your driver with Envy

---

### Post by joakim2008 on 2007-10-22
thanx. i'll try that and make a post after that to tell you the results ..... or unhopefully asking for another solution.


if you need any other config or error file to diagnose my problem just ask it. 

i have 2 days working on this and i feel really stupid...  :( i have read all around in forums and stuff but still no answer...

i' ll try that and come back soon !

---

### Post by alb@nian on 2007-10-22
Rconfigure all the drivers

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by joakim2008 on 2007-10-22
> **dynamethod said:**
> yeah give it another try, but after you uninstall the driver with Envy, try a reboot and THEN install your driver with Envy

I tried to install the NVIDIA driver automatically but in the envy.installer.log says that NVIDIA card not found



If I try manually is there a problem ? What is going on with my graphic card ????

---

### Post by dynamethod on 2007-10-22
> **alb@nian said:**
> Rconfigure all the drivers

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

open up a terminal and type the above code into it, then try reboot

---

### Post by joakim2008 on 2007-10-22
for the X server should I use "nv" driver or something else?

---

### Post by dynamethod on 2007-10-22
try it, if 'nv' doesnt work, try 'vesa'

---

### Post by joakim2008 on 2007-10-22
ENVY can't install the NVIDIA drivers itself... I have to do it manually... should i try it or not ? Is there anything else wrong ?

---

### Post by joakim2008 on 2007-10-22
i tried nv for the X server. It only asked me for driver for X server and resolution and nothing else in the previous code you told me to use.


Is there anything else i supposed to wait for config there except for those two settings ?

---

### Post by joakim2008 on 2007-10-22
anyone ?

---

### Post by beaudoin996 on 2007-10-22
I have the same video card.  

```
lspci |grep -ri vga
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
```

If I active the nvidia card with the restricted driver manager, the X server fall in safe mode.

I'm trying to enable the 3D acceleration. It worked well with feisty and the problem is caused with  the gutsy update.

---

### Post by joakim2008 on 2007-10-23
I reinstalled Ubuntu from the beginning so that everything resets to normal. I installed Ubuntu through Virtual PC and under Safe Graphics Mode. I enabled Universe and Multiverse repositories and i am waiting for instructions installing GeForce 6600, if anyone is eager to help...


Please ..>!

---

### Post by joakim2008 on 2007-10-23
i used 

```
lspci |grep -ri vga
```

and the terminal showed this

```
00:80.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+]
```


But my card is NVIDIA ... !

---

### Post by joakim2008 on 2007-10-23
please... anyone ? ... i am in a total mess up !

thanx

---

### Post by bardic on 2007-10-23
I would like to add my voice to this plea for help. 
I have a nVida 6600, and right now it's using the generic vesa(?...at work so I can't check at the moment) drivers. When browsing around my monitor/card options I noticed I could manually select my driver. 
I seen the nVida 6 series driver so I select that, but xserver died.  I couldn't figure it out and needed to partition so I just reinstalled...

Also, what is ENVY that everyone was talking about?

---

### Post by HMartinho on 2007-10-23
Hi guys;

I also have an nVidia 6600 card, try to do what I did and check if it helped out:
Configure your update optins to access restricted drivers also, that will install the nvidia-glx-new driver and thus use the propietary drivers from nvidia, unninstall everything else like envy and such, enable restricted drivers did it for me, by the way, I'm a 2 day noob so sorry I can't give more detailed info.
Do not use the nv driver, look for a driver named nvidia, elseway you won't get the desktop effects running.

Hope this helps.

Cheers.

---

### Post by steve.horsley on 2007-10-23
Is it possible that the BIOS is set to use the built-in S3 controller and is disabling your addidional nVidia card? Perhaps look in the BIOS setup and see if you have to enable the nVidia card, or disable the on-board graphics.

I have a 6600GT, and simply installing the package nvidia-glx-new made it work beautifully.

---

### Post by joakim2008 on 2007-10-23
you think it's BIOS? interesting. the fact i am using Virtual PC counts on any prob ?

---

### Post by snkmad on 2007-10-23
You installing Ubuntu over Virtual PC?
Then itll never see you Geforce 6600...
That S3 GFX card is the one Virtual PC emulate.

---

### Post by NotTheMessiah on 2007-10-23
> **snkmad said:**
> You installing Ubuntu over Virtual PC?
Then itll never see you Geforce 6600...
That S3 GFX card is the one Virtual PC emulate.

Bingo :guitar:

---

### Post by beaudoin996 on 2007-10-23
> **HMartinho said:**
> Hi guys;

I also have an nVidia 6600 card, try to do what I did and check if it helped out:
Configure your update optins to access restricted drivers also, that will install the nvidia-glx-new driver and thus use the propietary drivers from nvidia, unninstall everything else like envy and such, enable restricted drivers did it for me, by the way, I'm a 2 day noob so sorry I can't give more detailed info.
Do not use the nv driver, look for a driver named nvidia, elseway you won't get the desktop effects running.

Hope this helps.

Cheers.

I'm suprised it works for you because it doesn't for me.  Are you using gutsy ? What happenned when you type :

```

lspci |grep -ri vga

```

---

