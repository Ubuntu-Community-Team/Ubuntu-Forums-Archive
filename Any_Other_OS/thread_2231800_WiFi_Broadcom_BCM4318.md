---
title: "WiFi Broadcom BCM4318"
date: 2014-06-28
forum: Any Other OS
---

### Post by dennis24 on 2014-06-28
Hello, im new to this form, in fact i made this account just to get help with this problem. I have an  Acer Aspire 5100 which i wiped clean and installed Debian onto. But when i load it up and i go to connect to the Wireless network, it only shows me a wired connection. Now iv been trying to figure out why i cant get wireless for about a week now but with no luck. I am pretty sure it is because i don't have the right drive or something. I have no idea how to fix this and am a vary novice user to Debian (And any other Linux based system) So if anyone can help it would be a AMAZING! Thanks
PS~ I also cant connect to any internet on that computer but i can use another one and transfer a file over to the broken one if need-be

---

### Post by Irihapeti on 2014-06-28
*Thread moved to **Networking & Wireless**.*

---

### Post by 3rdalbum on 2014-06-28
This is the Ubuntu forum, not the Debian forum. The two systems are similar but not identical.

On Ubuntu, you would run the Software & Updates program, click Additional Drivers and it would offer to download firmware for the Broadcom wireless card.

On Debian you probably have to manually download it and install it.

Debian is great but new users would usually be better served with Ubuntu or some other distro that makes life easier for the user. If you want to stick with Debian, try asking on a Debian forum site or the Other OS forum on here.

---

### Post by kc1di on 2014-06-28
here is a [Debian page]("https://wiki.debian.org/bcm43xx") that may be of help to you.

---

### Post by Bucky Ball on 2014-06-28
*Thread moved to **Other OS/Distro Support**.*

Welcome.

> **3rdalbum said:**
> This is the Ubuntu forum, not the Debian forum. The two systems are similar but not identical.



This. You would be best posting on a Debian forum as well as here.

---

### Post by dennis24 on 2014-06-28
OK. Thanks for the help but i gess ill switch the system over to Ubuntu then and try what "3rdalbum" said because im so new to linux and Ubuntu sound to be a lot easier to use. So thank you for all your help again

---

### Post by kc1di on 2014-06-28
> **dennis24 said:**
> OK. Thanks for the help but i gess ill switch the system over to Ubuntu then and try what "3rdalbum" said because im so new to linux and Ubuntu sound to be a lot easier to use. So thank you for all your help again

I Think you'll like it  :)

---

### Post by dennis24 on 2014-06-28
Ya lets hope im putting it onto a live USB to install now

---

### Post by dennis24 on 2014-06-28
ok now i seem to be still having the same problem and have tried to fix it for about 3-4 hours now but with no luck. i still think that the driver is messed up but dont know how to fix it without internet on that computer.

---

### Post by dennis24 on 2014-06-28
OK now i seem to be still having the same problem and have tried to fix it for about 3-4 hours now but with no luck. I still think that the driver is messed up but don't know how to fix it without internet on that computer.
I ran a wireless script and this is what i got &#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;
```

#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#


FILEBASE="wireless-info"
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5|6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etwork)[^[:punct:] ]*"


exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCannot write output file, aborting.\n\n"
    exit 1
fi


printf "\n########## wireless info START ##########\n"


printf "\n##### release #####\n\n"
lsb_release -idrc


printf "\n##### kernel #####\n\n"
uname -a


printf "\n##### lspci #####\n\n"
lspci -nnk | grep -iA2 net | sed 's/^--$//'


printf "\n##### lsusb #####\n\n"
lsusb


printf "\n##### PCMCIA Card Info #####\n\n"
pccardctl info


printf "\n##### rfkill #####\n\n"
rfkill list all


printf "\n##### lsmod #####\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"


printf "\n##### iw reg get #####\n\n"
iw reg get


printf "\n##### interfaces #####\n\n"
sed 's/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces


printf "\n##### iwconfig #####\n\n"
iwconfig


printf "\n##### route #####\n\n"
route -n


printf "\n##### resolv.conf #####\n\n"
grep -v '^#' /etc/resolv.conf


printf "\n##### nm-tool #####\n"
nm-tool


printf "\n##### NetworkManager.state #####\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state


printf "\n##### NetworkManager.conf #####\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi


printf "\n##### iwlist #####\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi


printf "\n##### iwlist channel #####\n\n"
iwlist chan


printf "\n##### modinfo #####\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done


printf "\n##### modules #####\n\n"
grep -v '^#' /etc/modules


printf "\n##### blacklist #####\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
	BLACKLIST=$(grep '^blacklist' $CONFFILE)
	if [ -n "$BLACKLIST" ]; then
	    printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
	fi
    fi
done


printf "\n##### udev rules #####\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules


printf "\n##### dmesg #####\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"


printf "\n########## wireless info END ############\n\n"


exec 1>&3 3>&-
exec 2>&4 4>&-


RESULTS=$(cat -s $FILEBASE.txt)
sed 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' <<< "$RESULTS" > $FILEBASE.txt


if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

```

If thats any help to you

---

### Post by dennis24 on 2014-06-28
OK now i seem to be still having the same problem and have tried to fix it for about 3-4 hours now but with no luck. I still think that the driver is messed up but don't know how to fix it without internet on that computer.
I ran a wireless script and this is what i got &#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;

```

#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#


FILEBASE="wireless-info"
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5|6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etwork)[^[:punct:] ]*"


exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCannot write output file, aborting.\n\n"
    exit 1
fi


printf "\n########## wireless info START ##########\n"


printf "\n##### release #####\n\n"
lsb_release -idrc


printf "\n##### kernel #####\n\n"
uname -a


printf "\n##### lspci #####\n\n"
lspci -nnk | grep -iA2 net | sed 's/^--$//'


printf "\n##### lsusb #####\n\n"
lsusb


printf "\n##### PCMCIA Card Info #####\n\n"
pccardctl info


printf "\n##### rfkill #####\n\n"
rfkill list all


printf "\n##### lsmod #####\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"


printf "\n##### iw reg get #####\n\n"
iw reg get


printf "\n##### interfaces #####\n\n"
sed 's/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces


printf "\n##### iwconfig #####\n\n"
iwconfig


printf "\n##### route #####\n\n"
route -n


printf "\n##### resolv.conf #####\n\n"
grep -v '^#' /etc/resolv.conf


printf "\n##### nm-tool #####\n"
nm-tool


printf "\n##### NetworkManager.state #####\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state


printf "\n##### NetworkManager.conf #####\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi


printf "\n##### iwlist #####\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi


printf "\n##### iwlist channel #####\n\n"
iwlist chan


printf "\n##### modinfo #####\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done


printf "\n##### modules #####\n\n"
grep -v '^#' /etc/modules


printf "\n##### blacklist #####\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
	BLACKLIST=$(grep '^blacklist' $CONFFILE)
	if [ -n "$BLACKLIST" ]; then
	    printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
	fi
    fi
done


printf "\n##### udev rules #####\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules


printf "\n##### dmesg #####\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"


printf "\n########## wireless info END ############\n\n"


exec 1>&3 3>&-
exec 2>&4 4>&-


RESULTS=$(cat -s $FILEBASE.txt)
sed 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' <<< "$RESULTS" > $FILEBASE.txt


if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

```

If thats any help

---

### Post by kc1di on 2014-06-28
you'll need to find a way to connect via ethernet cable until you get the drivers for you Card.

[here's a page]("http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/") that will be of help.

---

### Post by Bucky Ball on 2014-06-28
Are you trying to do this with booting from the disk and not a hard drive install? If so, that is probably why you're having problems. Install Ubuntu, then tackle the problem. That card should work in no time with a full install. Broadcom are well supported. 

Just out of curiosity, what do you have in Additional Drivers? As mentioned, if you could get an ethernet cable into that machine and get online that card would probably be working already.

---

### Post by ptn107 on 2014-06-29
If your using Debian 7 install this: [_firmware-brcm80211_0.41~bpo70+1_all.deb_]("http://ftp.us.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-brcm80211_0.41~bpo70+1_all.deb")
for Debian 6 install this: [_firmware-brcm80211_0.36+wheezy.1~bpo60+1_all.deb_]("http://ftp.jp.debian.org/debian-backports/pool/non-free/f/firmware-nonfree/firmware-brcm80211_0.36+wheezy.1~bpo60+1_all.deb")

reboot

---

