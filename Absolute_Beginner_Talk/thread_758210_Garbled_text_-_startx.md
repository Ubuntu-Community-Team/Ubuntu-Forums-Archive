---
title: "Garbled text - startx?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2008-04-17
Okay, here goes.

Laptop with  Ubuntu on. It's booted fine for months. 6.06 I do believe.  The text and startup splash screen have always been "garbled" - unable to read.    But that sorted itself out by the time the mouse came on screen.

Well, it's just decided to stop reaching that point.  It gets to a command line. I don't know what it's saying.

I'm trying "startx", but it's not actually doing it.  I remember there was a file you had to delete first before that would work?  I don't know.  But it's not starting properly and I don't know what I should do.

Help please?

---

### Post by unutbu on 2008-04-17
What happens when you press CTRL-ALT-F2? Do you get a virtual (text) console that you can read, or is it also messed up?

---

### Post by st33med on 2008-04-17
I have had problems like this as well... The garbled text will appear during shutdown, and the shell never shows.

If there is a solution, do tell.

---

### Post by Neon_Knight on 2008-04-18
I get a flashing cursor with ctrl+alt+F2. It's an elongated, stretched, garbled cursor.  But it's a cursor.  Nothing I type has any response, as in, no letters come up at all, pressing keys does nothing.

---

### Post by unutbu on 2008-04-18
What happens when you boot from a rescue CD? The Ubuntu Live CD perhaps?

---

### Post by Neon_Knight on 2008-04-18
It works perfectly fine with the 6.06 live CD.  In fact, that's what I'm using at the moment.

Help?  I have files on there I'd like to keep..

And I'd really like my old system back with all of my programs.. 

So...what can I do?  What is the file that I have to delete before startx can work properly?

---

### Post by unutbu on 2008-04-18
Okay, this is a shot in the dark, but since no one has posted a better suggestion so far, here goes...

You haven't used your computer a heck of a lot in the last 21 hours -- you might have booted a lot, but very few files other than /proc, /dev and such have probably changed. So, what if we ask for a list of all the files that have been modified in the last 24 hours? (Estimate how long it has been since your machine was working properly).

Boot from the Live CD.

mount your hard drive at /media/disk.

sudo find /media/disk -mmin -1440 > changed-files

changed-files will then have a list of all the files that have been modified in the last 24 hours (24*60=1440 minutes). 

If your problem is caused by a file that has been improperly added or modified in the last 24 hours, it will be listed there. If the problem is due to a file having been deleted, then you'll need to find out what package you need to re-install. Unfortunately, I have no idea what that might be.

changed-files will be rather long and have a lot of /proc and /sys and /dev lines which you can probably ignore. If you can run perl, this script will filter out those lines, leaving you with a more manageable list:


```
#!/usr/bin/perl
use strict;
use warnings;

open(FILE,"<","changed-files") || die;
while (<FILE>) {
    if (!(m|^/dev| or m|^/sys| or m|^/proc| or m|^find:|)) {
	print;
    }
}
close(FILE)

```

---

### Post by Neon_Knight on 2008-04-18
okay, I've done that, set it to 96 hours, and I've typed "perl" into the console and pasted that lot in..     now what? How do I get the perl script to run?

---

### Post by Neon_Knight on 2008-04-18
Well, here's the file anyway.   I think 96 hours is a bit much, as you can see aMSN files modified.  (But that could have been me trying to access them earlier, to see in the chat logs when I last logged on, to find out when it stopped working, but that failed)

```

/media/disk/var/backups
/media/disk/var/cache/cups/remote.cache
/media/disk/var/cache/cups/job.cache
/media/disk/var/cache/man
/media/disk/var/cache/man/local
/media/disk/var/cache/man/oldlocal
/media/disk/var/lib/acpi-support/system-manufacturer
/media/disk/var/lib/acpi-support/system-product-name
/media/disk/var/lib/acpi-support/system-version
/media/disk/var/lib/acpi-support/bios-version
/media/disk/var/lib/apt/lists
/media/disk/var/lib/apt/lists/partial
/media/disk/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_Release.gpg
/media/disk/var/lib/apt/lists/lock
/media/disk/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_Release
/media/disk/var/lib/dhcp3/dhclient.eth1.leases
/media/disk/var/lib/dhcp3/dhclient.eth2.leases
/media/disk/var/lib/dhcp3/dhclient.ath0.leases
/media/disk/var/lib/dhcp3/dhclient.wlan0.leases
/media/disk/var/lib/dhcp3/dhclient.eth0.leases
/media/disk/var/lib/dpkg/lock
/media/disk/var/lib/gdm
/media/disk/var/lib/gdm/.gdmfifo
/media/disk/var/lib/gdm/.cookie
/media/disk/var/lib/gdm/:0.Xauth
/media/disk/var/lib/gdm/:0.Xservers
/media/disk/var/lib/logrotate/status
/media/disk/var/lib/slocate
/media/disk/var/lib/slocate/slocate.db
/media/disk/var/lib/urandom
/media/disk/var/lib/urandom/random-seed
/media/disk/var/lib/xkb
/media/disk/var/log
/media/disk/var/log/cups
/media/disk/var/log/cups/error_log
/media/disk/var/log/cups/error_log.1.gz
/media/disk/var/log/gdm
/media/disk/var/log/gdm/:0.log
/media/disk/var/log/gdm/:0.log.1
/media/disk/var/log/auth.log
/media/disk/var/log/lastlog
/media/disk/var/log/scrollkeeper.log
/media/disk/var/log/syslog
/media/disk/var/log/wtmp
/media/disk/var/log/evms-engine.log
/media/disk/var/log/dmesg
/media/disk/var/log/udev
/media/disk/var/log/acpid
/media/disk/var/log/daemon.log
/media/disk/var/log/kern.log
/media/disk/var/log/user.log
/media/disk/var/log/debug
/media/disk/var/log/messages
/media/disk/var/log/Xorg.0.log
/media/disk/var/log/syslog.0
/media/disk/var/log/evms-engine.1.log
/media/disk/var/log/Xorg.0.log.old
/media/disk/var/log/acpid.1.gz
/media/disk/var/spool/anacron/cron.daily
/media/disk/var/spool/anacron/cron.monthly
/media/disk/etc
/media/disk/etc/lvm/.cache
/media/disk/etc/motd
/media/disk/etc/mtab
/media/disk/etc/printcap
/media/disk/etc/resolv.conf
/media/disk/home/david
/media/disk/home/david/.Xauthority
/media/disk/home/david/.xsession-errors
/media/disk/home/david/.gconf
/media/disk/home/david/.gconf/desktop/gnome/peripherals/keyboard/host-david-laptop/0
/media/disk/home/david/.gconf/desktop/gnome/peripherals/keyboard/host-david-laptop/0/%gconf.xml
/media/disk/home/david/.gconf/apps/panel/applets/clock_screen0/prefs
/media/disk/home/david/.gconf/apps/panel/applets/clock_screen0/prefs/%gconf.xml
/media/disk/home/david/.gconf/apps/panel/applets/workspace_switcher_screen0/prefs
/media/disk/home/david/.gconf/apps/panel/applets/workspace_switcher_screen0/prefs/%gconf.xml
/media/disk/home/david/.gconf/apps/panel/applets/window_list_screen0/prefs
/media/disk/home/david/.gconf/apps/panel/applets/window_list_screen0/prefs/%gconf.xml
/media/disk/home/david/.gconf/apps/evolution
/media/disk/home/david/.gconf/apps/evolution/%gconf.xml
/media/disk/home/david/.gconfd
/media/disk/home/david/.gconfd/saved_state
/media/disk/home/david/.gnome2/share/fonts/fonts.dir
/media/disk/home/david/.gnome2/share/cursor-fonts/fonts.dir
/media/disk/home/david/.ICEauthority
/media/disk/home/david/.metacity/sessions
/media/disk/home/david/.metacity/sessions/1208250324-4784-2990229643.ms
/media/disk/home/david/.metacity/sessions/1208252545-5493-3497928957.ms
/media/disk/home/david/.amsn/gconfig.xml
/media/disk/home/david/.amsn/profiles
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/plugins.xml
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/config.xml
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/smileys/cache
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/smileys/cache/45153446035584971677078674f674e4a64513059766552416d483d3.png
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/abook.xml
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/f6448627547494a637b6655336a45413238446144466d4843514f6d3.png
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/f6448627547494a637b6655336a45413238446144466d4843514f6d3.dat
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/9525b65705a77454465634551475868763c4a543835747533375f6d3.png
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/9525b65705a77454465634551475868763c4a543835747533375f6d3.dat
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/9594378685b2e69753353615f4c423f634051323332777f2730336d3.png
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/7357455727366424b617030783a696e4d4d6b4e6076336f664d676d3.png
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/9594378685b2e69753353615f4c423f634051323332777f2730336d3.dat
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/7357455727366424b617030783a696e4d4d6b4e6076336f664d676d3.dat
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/64e6e6b617c6835414171366d6c427a4a54576830793944365f414d3.png
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/64e6e6b617c6835414171366d6c427a4a54576830793944365f414d3.dat
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/4516a535f644f664d644e6167424c6832783a55484953464278677d3.png
/media/disk/home/david/.amsn/The_Neon-knight_hotmail_com/displaypic/cache/4516a535f644f664d644e6167424c6832783a55484953464278677d3.dat
/media/disk/home/david/.evolution
/media/disk/home/david/.evolution/mail/local/Inbox.ibex.index
/media/disk/home/david/.evolution/mail/local/Inbox.ibex.index.data
/media/disk/home/david/.evolution/mail/local/Drafts.ibex.index
/media/disk/home/david/.evolution/mail/local/Drafts.ibex.index.data
/media/disk/home/david/.evolution/mail/local/Outbox.ibex.index
/media/disk/home/david/.evolution/mail/local/Outbox.ibex.index.data
/media/disk/home/david/.evolution/mail/local/Sent.ibex.index
/media/disk/home/david/.evolution/mail/local/Sent.ibex.index.data
/media/disk/home/david/.evolution/secmod.db
/media/disk/home/david/.evolution/cert8.db
/media/disk/home/david/.evolution/key3.db
/media/disk/tmp
/media/disk/tmp/.X11-unix
/media/disk/tmp/.X11-unix/X0
/media/disk/tmp/.ICE-unix
/media/disk/tmp/.ICE-unix/4717
/media/disk/tmp/.ICE-unix/5436
/media/disk/tmp/.gdm_socket
/media/disk/tmp/orbit-david
/media/disk/tmp/orbit-david/linc-156c-0-5b428d6cfaf4
/media/disk/tmp/orbit-david/linc-153c-0-3fdb178adb06e
/media/disk/tmp/orbit-david/bonobo-activation-register.lock
/media/disk/tmp/orbit-david/linc-1571-0-4449bb6338272
/media/disk/tmp/orbit-david/bonobo-activation-server-ior
/media/disk/tmp/orbit-david/linc-1575-0-28857111f5c8
/media/disk/tmp/orbit-david/linc-157a-0-34d4a9e05b579
/media/disk/tmp/orbit-david/linc-1580-0-237e046136637
/media/disk/tmp/orbit-david/linc-12b9-0-279c2cc1a5ffc
/media/disk/tmp/orbit-david/linc-1584-0-237e04619e164
/media/disk/tmp/orbit-david/linc-1582-0-237e0461c0408
/media/disk/tmp/orbit-david/linc-1588-0-508a90958352d
/media/disk/tmp/orbit-david/linc-1594-0-149b38d1ad260
/media/disk/tmp/orbit-david/linc-158a-0-f0edd382d190
/media/disk/tmp/orbit-david/linc-1591-0-1835d7d9283dc
/media/disk/tmp/orbit-david/linc-15a5-0-75fda02696d6e
/media/disk/tmp/orbit-david/linc-12f1-0-1ff0d1d9cae23
/media/disk/tmp/orbit-david/linc-12f6-0-3195e07435a98
/media/disk/tmp/orbit-david/linc-15aa-0-64037881e77b8
/media/disk/tmp/orbit-david/linc-15ad-0-11d14affc85d1
/media/disk/tmp/orbit-david/linc-15b3-0-57001a10693ab
/media/disk/tmp/orbit-david/linc-15bd-0-24b9018579ee8
/media/disk/tmp/.X0-lock
/media/disk/tmp/ssh-XFdysV5436
/media/disk/tmp/ssh-XFdysV5436/agent.5436
/media/disk/tmp/gconfd-david
/media/disk/tmp/gconfd-david/lock
/media/disk/tmp/gconfd-david/lock/ior
/media/disk/tmp/keyring-xsCiyL
/media/disk/tmp/keyring-xsCiyL/socket
/media/disk/tmp/.esd-1000
/media/disk/tmp/.esd-1000/socket
/media/disk/tmp/mapping-david
/media/disk/tmp/virtual-david.W4KEif

```

Make anything of that?

---

### Post by unutbu on 2008-04-19
I see nothing here that might need changing.
Sorry. I'm out of ideas.

---

### Post by lswest on 2008-04-19
try this:
boot to a liveCD
then do (in a terminal) ```
sudo mkdir /media/linux/
sudo mount /dev/[name of your linux partition] /media/linux
sudo chroot /media/linux
sudo apt-get install --reinstall xserver-xorg
``` if that doesn't work, find your xorg.conf file (from /etc/X11/xorg.conf) and then edit the "Driver: " line to be Driver : "vesa", which should give you primitive graphics back.

The above codes make a mountpoint, mount the drive, make that new mountpoint (temporarily) the "/" (root filesystem) and re-installs the xserver.

---

### Post by cardinals_fan on 2008-04-19
> **Neon_Knight said:**
> 
I'm trying "startx", but it's not actually doing it.  I remember there was a file you had to delete first before that would work?  I don't know.  But it's not starting properly and I don't know what I should do.

Hit Ctrl-Alt-F4 and type the following three commands:
```
cd /tmp/
ls -A [COLOR="Red"]#Make sure that there is a file called .X0-lock[/COLOR]
sudo rm .X0-lock
```

---

### Post by Neon_Knight on 2008-04-21
> **lswest said:**
> try this:
boot to a liveCD
then do (in a terminal) ```
sudo mkdir /media/linux/
sudo mount /dev/[name of your linux partition] /media/linux
sudo chroot /media/linux
sudo apt-get install --reinstall xserver-xorg
``` if that doesn't work, find your xorg.conf file (from /etc/X11/xorg.conf) and then edit the "Driver: " line to be Driver : "vesa", which should give you primitive graphics back.

The above codes make a mountpoint, mount the drive, make that new mountpoint (temporarily) the "/" (root filesystem) and re-installs the xserver.

Neither of those worked, sorry. :(  

And neither did Cardinals' suggestion..

---

### Post by unutbu on 2008-04-21
Please post
```
sudo lshw -C video
cat /etc/X11/xorg.conf

```

---

### Post by Neon_Knight on 2008-04-21
> **unutbu said:**
> Please post
```
sudo lshw -C video
cat /etc/X11/xorg.conf

```

From logging on on the live CD, or in the garbled mode?

---

### Post by unutbu on 2008-04-21
Good idea. Let's copy both the Live CD's xorg.conf and yours.
So, please try the following:

Boot from Live CD,
Open terminal and run:

```

sudo lshw -C video > ~/lshw.out
cat /etc/X11/xorg.conf > ~/livecd-xorg.conf

sudo mkdir /media/linux      
sudo mount /dev/[name of your linux partition] /media/linux
cat /media/linux/etc/X11/xorg.conf > ~/garbled-xorg.conf

```

Post the contents of lshw.out, livecd-xorg.conf, and garbled-xorg.conf.

---

### Post by Neon_Knight on 2008-04-21
Okay, that all went without problems.

lshw.out
```

  *-display
       description: VGA compatible controller
       product: VT8623 [Apollo CLE266] integrated CastleRock graphics
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@01:00.0
       version: 03
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: iomemory:d8000000-dbffffff iomemory:de000000-deffffff irq:10

```

LiveCD xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Garbled xorg.conf

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```



There you go.  Can you make anything from that?

Cheers.




EDIT:

Oh, that "driver" in the garbled xorg.conf was changed to "vesa", as per one of the suggestions in this thread.

---

### Post by unutbu on 2008-04-21
Well, I know the display is garbled even outside of X, but if we could get X working again that would be an improvement, right?

So let's do the obvious thing and try using the Live CD's xorg.conf:

Boot the Live CD.

```
sudo mkdir /media/linux      
sudo mount /dev/[name of your linux partition] /media/linux
cd /media/linux/etc/X11
sudo mv xorg.conf garbled-xorg.conf
sudo cp /etc/X11/xorg.conf /media/linux/etc/X11

```

Reboot. Any better?

---

### Post by unutbu on 2008-04-21
I haven't read through it very carefully yet, but this link may contain an answer to your problem.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/197514](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/197514)

---

### Post by Neon_Knight on 2008-04-22
I tried your idea with the xorg.conf file.

It didn't help.

---

### Post by Neon_Knight on 2008-04-25
Any help, anybody?

---

