---
title: "MacBook Pro - Madwifi stops working after a few hours"
date: 2008-01-19
forum: Apple Intel Users
---

### Post by dvdkid919 on 2008-01-19
Hi.  I bought a brand new MacBook Pro about a week ago. I think it is called the "Santa Rosa" edition. It has the Atheros card and the nVidia GeForce 8600M GT.  I got Ubuntu 7.10 installed and I compiled the latest madwifi drivers from subversion.  Whenever I boot up into Ubuntu and log into GNOME, the network manager automatically connects to my network and everything is perfect... but after a few hours, my wireless connection to my router usually dies for some reason, and then I have trouble reconnecting.  I have not managed to ever reconnect to my router after this happens, without rebooting.  Rebooting always fixes it.  I have tried looking at a whole bunch of ubuntuforums.org pages that people had similar problems in, but none of their recommendations worked... even the ones that said [SOLVED].

lspci shows:
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

My /etc/rc.local has this at the bottom of it: 
modprobe ath_pci
modprobe wlan_scan_sta
iwpriv ath0 bgscan 0

And my /etc/modules has this in it (in addition to other irrelevant modules):
ath_pci
wlan_scan_sta

After I am disconnected with the router, I tried all of the usual commands, and none of them work... For example, I tried modprobing ath_pci and wlan_scan_sta, and doing iwpriv ath0 bgscan 0, iwlist ath0 scan, iwconfig ath0 essid, dhclient ath0, etc&#8230; Sometimes it doesn't even see ath0 as an interface and modprobing it doesn't help at all. Sometimes it sees ath0 but says it doesn't support scanning.  And sometimes it sees my SSID but when I try to connect it doesn't receive an IP from DHCP.

It's kind of annoying because I have to reboot several times a day.  I have never experienced any network problems while in OS X.

In case this could somehow help assist in the solving of this problem, I am experiencing the problem with my WEP-encrypted network, and am using an 802.11g router. (Linksys WRT54GS).

Any ideas? Any help is greatly appreciated.

---

### Post by devnater on 2008-01-19
this is a common issue and could have probably been found by searching...

anyway, the solution is most likely simply this:  
```
sudo iwpriv ath0 bgscan 0
```
(have to type it each boot or stick it in rc.local or something)

I use a slightly older madwifi trunk version (a month ago or so) and have no probs w/wifi.

---

### Post by dvdkid919 on 2008-01-19
I already have that in my /etc/rc.local, and it does execute at bootup... but it still stops working after a few hours. Anyone who has it working, could you possibly paste your entire: /etc/modules, /etc/rc.local, and /etc/network/interfaces? (If you have your network password in that then just change it to PASSWD or something.)

---

### Post by ekuefler on 2008-01-20
Hi,

I also got my MacBook Pro about a week ago. So far I've had zero trouble with WiFi. I followed the instructions from [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro), not doing anything special for Santa Rosa. Here are my files:

/etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
applesmc  #Fix for keyboard backlight

```

/etc/rclocal:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe ath_pci
modprobe wlan_scan_sta
iwpriv ath0 bgscan 0
exit 0

```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

```

Only changes I made to those files other than the backlight fix were straight from the instructions. Tell us if you find a solution.

---

### Post by cyberdork33 on 2008-01-20
make sure you blacklist the older madwifi module from the ubuntu-restricted.

I noticed you added "solved" to your first post. If this is now solved, please post your solution and mark the thread as solved from the "Thread Tools" menu at the top.

---

### Post by dvdkid919 on 2008-01-20
Well, it just happened again, and I decided to check my logs.
I noticed this:
```
Jan 20 03:35:24 MacbookPro kernel: [10835.803066] wifi0: rx FIFO overrun; resetting
Jan 20 03:35:28 MacbookPro kernel: [10837.857366] wifi0: rx FIFO overrun; resetting
Jan 20 03:35:31 MacbookPro kernel: [10840.063376] wifi0: rx FIFO overrun; resetting

```
That continues to output forever no matter what I do, until I reboot.

Looks like a whole bunch of other people are experiencing this problem too.
[http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017)

Is there any known solution? I already have "iwpriv ath0 bgscan 0" in /etc/rc.local at bootup.

---

### Post by cyberdork33 on 2008-01-20
> **dvdkid919 said:**
> Well, it just happened again, and I decided to check my logs.
I noticed this:
```
Jan 20 03:35:24 MacbookPro kernel: [10835.803066] wifi0: rx FIFO overrun; resetting
Jan 20 03:35:28 MacbookPro kernel: [10837.857366] wifi0: rx FIFO overrun; resetting
Jan 20 03:35:31 MacbookPro kernel: [10840.063376] wifi0: rx FIFO overrun; resetting

```That continues to output forever no matter what I do, until I reboot.

Looks like a whole bunch of other people are experiencing this problem too.
[http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017)

Is there any known solution? I already have "iwpriv ath0 bgscan 0" in /etc/rc.local at bootup.
If the solution is not in the bug report then there probably isn't one yet.

---

### Post by bsantos on 2008-04-23
Since a suspend cycle now reloads the network modules, we need to rerun this command on resume.

I use the following script /etc/pm/sleep.d/99athfix

```

#!/bin/bash

. /usr/lib/pm-utils/functions

resume_athfix()
{
  (sleep 10 && iwpriv ath0 bgscan 0) &
}

case "$1" in
    resume)
        resume_athfix
        ;;
    *)
        ;;
esac

exit $?

```I sleep for 10 seconds waiting for the private ioctls to be available then issue the command disabling bgscan.

If bgscan was preventing the overruns this will keep it working after suspending and hibernating.

---

### Post by rytmisk on 2008-06-09
Hi

According to [http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017) the issue is now fixed, but as I say at the bottom, there is no way any unexperienced user such as myself can make this work. There is a reference to a patch and a change in modprobe:conf which I have no idea of how to apply. 

Can anyone help?

Best regards
Ketil Thorgersen

---

### Post by cyberdork33 on 2008-06-11
Please post in the the new Apple Users forum, this is just an archive.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

