---
title: "Broadcom driver for 4328 b/g/n wireless device"
date: 2008-09-09
forum: Apple Hardware Users
---

### Post by hajk on 2008-09-09
I just want to report here that I've finally gotten the Broadcom 4328 (rev 05) wireless device in my MacBook Pro 4,1 (Penryn) to function properly, now using the new Broadcom Linux *wl* driver available at their website [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php). It works both in mixed 802.11b/g/n and in pure 802.11n (draft) mode, in the 2.4 and 5GHz bands, and with WPA2 Personal security (CCMP-AES).

Compiling is easy (I had already a proper compiling setup with the module-assistant package and the "sudo m-a prepare" command). I copied the wl.ko driver file to /lib/modules/2.6...../misc, then ran "sudo depmod -a". Broadcom claim that this module, once compiled, is "version-agnostic" and should work with all 2.6 kernels, so keep a copy around somewhere.

This new Broadcom driver, a Linux wrapper really around a Broadcom proprietary binary, suffers from the same interference by *ssb* that Ndiswrapper does. So, make sure to load *wl* before *ssb*. I do that through the script /usr/local/bin/wireless```

#!/bin/sh
rmmod wl ssb
modprobe wl
modprobe ssb
```
made executable with the "sudo chmod a+x" command and added to /etc/rc.local.

Throughput is fine, but reported connection strength behaves in a funny way: the network-manager icon is fully blue at first, indicating 100% signal strength (OK, next to the AP), but then becomes white at 0%. Clicking on the icon shows my network bar 100% blue. Also the "sudo iwconfig" command shows speeds between 1 and 53Mb/s. Also, the connection drops after a period of inactivity, but comes back up promptly when loading some web page -- this is probably a feature to preserve battery power.

All told, I'm well pleased with the performance, so I'll get rid of Ndiswrapper.:guitar:

---

### Post by kosumi68 on 2008-09-09
This is very good news! I can confirm the 32-bit driver working on an MBA. However, as you state, the status indications are behaving oddly; iwconfig does not seem to always report the AP state. Also, I am not sure if the power consumption went up or down. Clearly some things needs fixing, but it works!

---

### Post by cyberdork33 on 2008-09-09
> **kosumi68 said:**
> This is very good news! I can confirm the 32-bit driver working on an MBA. However, as you state, the status indications are behaving oddly; iwconfig does not seem to always report the AP state. Also, I am not sure if the power consumption went up or down. Clearly some things needs fixing, but it works!

I heard about the wl driver but hadn't seen it in the wild. I will try to test tonight, maybe throw some debs together... Do they have anywhere to report bugs or give feedback?

---

### Post by cyberdork33 on 2008-09-10
This is in L-R-M in Intrepid! It is not setup to blacklist b43 and ssb automatically though. (I think ssb is not required and is only used by b43 / b43-legacy)

Enable wl in System > Adminstration > Hardware Drivers

add 'wl' to /etc/modules

Add the following to /etc/modprobe.d/blacklist
```
blacklist b43
```

Then I used a script similar to the above to load the modules in the correct order.

---

### Post by _mario_ on 2008-09-10
Hi,

the wl driver is also available in the linux-restricted-modules package in Hardy. The version in 2.6.24-19 doesn't yet support newer chips, but the version in 2.6.24-20/2.6.24-21 do (enable the hardy-proposed repository). Both additionally include the broadcom driver for the synaptics touchpad. I had to blacklist some modules, as the original documentation states.

Note: The version in 2.6.24-21 has a small bug: a required symbol doesn't match the provided version in the kernel package. It nevertheless works like a charm. :-)

This yields the following /etc/modprobe.d/wl file:
```

# blacklist unwanted modules for wl to work
blacklist ssb
blacklist b43
blacklist b43legacy
blacklist ndiswrapper

# ignore symbols' versions (necessary on 2.6.24-21)
install wl /sbin/modprobe --ignore-install --force-modversion wl $CMDLINE_OPTS

```

Don't forget to run:
```

update-initramfs -k all -u

```
if you change something in /etc/modprobe.d (the initial ramdisk contains copies of these files). Otherwise the interfering modules are loaded at next reboot.

Thanks to Ubuntu, there's no need to compile.

---

### Post by cyberdork33 on 2008-09-10
> **_mario_ said:**
> (enable the hardy-proposed repository).

Before anyone does this, note that enabling the proposed repository opens up a LOT of "unstable" software other than the Linux kernel. There is no need for a normal user to do that, but if you know what you are doing and are willing to deal with broken / buggy apps, go right ahead.

---

### Post by _mario_ on 2008-09-10
> **cyberdork33 said:**
> Before anyone does this, note that enabling the proposed repository opens up a LOT of "unstable" software other than the Linux kernel. There is no need for a normal user to do that, but if you know what you are doing and are willing to deal with broken / buggy apps, go right ahead.

Thanks. I forgot to mention that. For those who nevertheless want to use these newer kernel versions, there's a safer method:

1. Enable hardy-proposed
2. Set its priority so 1, similar to experimental in Debian by creating /etc/apt/preferences with:
```

Package: *
Pin: release o=Ubuntu,a=hardy-proposed
Pin-Priority: 1

```
(see man apt_preferences). Thus, apt will never choose to install packages from this repository.
3. Use
```

apt-get install --target-release hardy-proposed <package name>

```
to install specific packages from this repository.

ciao,
Mario

---

### Post by hajk on 2008-09-10
Well, that's just great! I don't know how I could have missed that Broadcom module... the latest version has been out since 1st of July 2008. But then that Linksys WUSB54GC adapter worked so well (only problem was mechanical: would fit only on the RHS of my MBP where it got easily bent since I'm right-handed). 

I'm planning to do an upgrade to Ibex (?) Intrepid (?) 8.10 (?) soon...
About blacklisting ssb: that's no good if you want to use the mini cardslot on a MBP, since the pcmcia module needs it. In that case, make sure wl gets loaded before ssb does.

---

### Post by cyberdork33 on 2008-09-10
> **_mario_ said:**
> I forgot to mention that. For those who nevertheless want to use these newer kernel versions, there's a safer method

Thanks for the detail. That will be helpful.

> **hajk said:**
> Well, that's just great! I don't know how I could have missed that Broadcom module... the latest version has been out since 1st of July 2008. But then that Linksys WUSB54GC adapter worked so well (only problem was mechanical: would fit only on the RHS of my MBP where it got easily bent since I'm right-handed). 

I'm planning to do an upgrade to Ibex (?) Intrepid (?) 8.10 (?) soon...
About blacklisting ssb: that's no good if you want to use the mini cardslot on a MBP, since the pcmcia module needs it. In that case, make sure wl gets loaded before ssb does.Hey, I didn't know about it either...

OK, everything I was seeing was indicating that ssb is really "part of" the b43 set. I didn't know it was used for other things. I will edit.

---

### Post by hajk on 2008-09-10
.

---

### Post by _mario_ on 2008-09-11
Yes, there's indeed more fun with ssb and pcmcia than expected.

(a) Kernel 2.6.24-21 loads ssb _only_ if it is _not_ blacklisted:
```

mario@snoopy:~> uname -a
Linux snoopy 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
mario@snoopy:~> lsmod | grep ssb
ssb                    56324  0
pcmcia                 45976  1 ssb
pcmcia_core            46116  2 ssb,pcmcia

```
Thus, the ssb module needs pcmcia. Not the other way around (see modinfo pcmcia pcmcia_core). This is consistent with:
```

mario@snoopy:~> lspci -nn | grep -i broadcom
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)
mario@snoopy:~> modinfo ssb
filename:       /lib/modules/2.6.24-21-generic/updates/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     F6D0BAEFF33F8EC859E8E6F
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        pcmcia_core,pcmcia
vermagic:       2.6.24-21-generic SMP mod_unload

```
Because the ssb module claims to support this device (2nd alias line) and
states that it needs pcmcia (depends line).

(b) Kernel 2.6.24-20 loads ssb _even_ if it _is_ blacklisted:
```

mario@snoopy:~> uname -a
Linux snoopy 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux
mario@snoopy:~> lsmod | grep ssb
ssb                    56836  0
pcmcia                 45976  1 ssb
pcmcia_core            46116  2 ssb,pcmcia
mario@snoopy:~> lspci -nn | grep -i broadcom
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)
mario@snoopy:~> modinfo ssb
filename:       /lib/modules/2.6.24-20-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     279FA7796EFE6F6E32CEB5C
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:
vermagic:       2.6.24-20-generic SMP mod_unload

```
I really don't know why. The module doesn't drive this device (missing alias), nor does it need pcmcia (missing depends).

(c) Kernel 2.6.24-19 _never_ loads ssb even if it is _not_ blacklisted:
```

mario@snoopy:~> uname -a
Linux snoopy 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
mario@snoopy:~> lsmod | grep ssb
mario@snoopy:~> lsmod | grep pcmcia
mario@snoopy:~> lspci -nn | grep -i broadcom
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)
mario@snoopy:~> modinfo ssb
filename:       /lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     279FA7796EFE6F6E32CEB5C
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:
vermagic:       2.6.24-19-generic SMP mod_unload

```
This is consistent again.

For those kernels that load ssb and pcmcia (probably newer versions in Intrepid too) it is safe to unload (or blacklist) ssb without affecting pcmcia if needed for something else.

After all, it's probably best to use 2.6.24-21 which works out-of-the-box (with ssb blacklisted) or use 2.6.24-19 after compiling wl manually.

ciao,
Mario

---

### Post by hajk on 2008-09-11
Interesting...although I don't know enough of this topic to confirm it one way or the other. Blacklisting ssb or loading it in the right order, either way won't hurt then, as I understand you properly.

---

### Post by cyberdork33 on 2008-09-11
My guess is some sort of interdependency for pcmcia wifi cards.

Other than using resources, it really don't matter either way (besides there are probably other modules worth unloading before ssb.

---

### Post by hajk on 2008-09-11
I've done a bit more trial-and-error about the frequent disconnects using the new Broadcom wl driver. It turns out that it is a network-manager issue, with *dmesg* showing all sorts of problems about not going cleanly through all of five stages. So, I bypassed network-manager and configured the eth1 interface in /etc/network/interfaces,```

auto eth1
iface eth1 inet dhcp
   wpa-driver wext
   wpa-ssid XXXXXXXXX
   wpa-ap-scan 1
   wpa-proto WPA RSN
   wpa-pairwise CCMP
   wpa-group CCMP
   wpa-key-mgmt WPA-PSK
   wpa-psk "YYYYYYYYYY"
```(where I've masked my private data). I should note that WPA2 (or RSN, really) didn't work, but adding WPA did, connecting promptly on the first try. But the AP is in WPA2 Personal mode? The interface has been up for several hours now without a single disconnect, so I'm not complaining.

Now here's something else that's strange: the "sudo iwlist scan" command shows my interface up with pairwise and group CCMP security, as it should. But the "lsmod" command shows that only the "ieee80211_crypt_tkip" module is loaded as a dependency, not the "ieee80211_crypt_ccmp" module as one would expect. What gives?

---

### Post by jansongoh on 2008-09-12
hi, does this mean that do not have to use ndiswrapper as driver? means that monitor mode can be supported on bcm4328? 

I'm intending to run Backtrack 3 but the non support of monitor mode for bcm4328 on ndiswrapper makes this impossible. Or anyone has a tutorial on how to go about doing this?

All help appreciated!

---

### Post by cyberdork33 on 2008-09-12
> **jansongoh said:**
> hi, does this mean that do not have to use ndiswrapper as driver? means that monitor mode can be supported on bcm4328? 

I'm intending to run Backtrack 3 but the non support of monitor mode for bcm4328 on ndiswrapper makes this impossible. Or anyone has a tutorial on how to go about doing this?

All help appreciated!

You are probably not going to get much help here on sniffing.

The wl driver is provided by Broadcom and should support all the functions that their drivers for Windows allow. So, yes, you do not have to use ndiswrapper to use this driver.

---

### Post by robzon on 2008-09-15
The driver works but leaves a lot to be wished for.
I did some simple benchmarking - tried to download a file over http from my local network.

On ndiswrapper I got consistent speed of 3.5MB/s.
On wl the speed varies between 0.5MB/s and 1.5MB/s.

Huge difference! Additionally ad-hoc, master and monitor modes do not work. I also couldn't change any settings related to power saving. Scanning for networks takes longer. Basically, everything I tested sucked compared to ndiswrapper. Still it DOES work and is usable (so far). For regular web browsing, chatting, etc it should be enough.

It's a huge step forward, but there's still plenty of work to do.

---

### Post by hajk on 2008-09-15
> **robzon said:**
> The driver works but leaves a lot to be wished for.
I did some simple benchmarking - tried to download a file over http from my local network.

On ndiswrapper I got consistent speed of 3.5MB/s.
On wl the speed varies between 0.5MB/s and 1.5MB/s.

Huge difference! Additionally ad-hoc, master and monitor modes do not work. I also couldn't change any settings related to power saving. Scanning for networks takes longer. Basically, everything I tested sucked compared to ndiswrapper. Still it DOES work and is usable (so far). For regular web browsing, chatting, etc it should be enough.

It's a huge step forward, but there's still plenty of work to do.
My ADSL connection gives me a max download speed of about 1750 kB/s and that's near what I got on average when downloading the Alpha-5 Intrepid install iso (took about 6-7 minutes). I get similar speeds during other downloads. Yet, the *reported* speed by iwconfig varies between 1 - 54 Mbps, basically a useless number. It seems to me that the problem is one of reporting, not of actual speed variation. And then the connection tends to time out after a period of non-use, like 15 minutes. I consider that a feature to save battery power. Anyway, I prefer it over having to insert some USB adapter...

---

### Post by cyberdork33 on 2008-09-15
yea I have seen a big improvement myself.

---

### Post by m.musashi on 2008-09-17
This is certainly good news and something I've been hoping for. However, could someone explain the exact steps to take to get this working via the kernel update (without running the risks involved with the proposed repo). I'm not a total newb or anything but this is my kids' computer and I'm tired of dealing work wifi issues every other day but I also don't want to make it worse. 

Thanks.

---

### Post by hajk on 2008-09-18
Have a look at the first sticky in the networking section of the Ubuntu Forums, it requires a kernel update from Hardy proposed.

---

### Post by cyberdork33 on 2008-09-18
> **m.musashi said:**
> This is certainly good news and something I've been hoping for. However, could someone explain the exact steps to take to get this working via the kernel update (without running the risks involved with the proposed repo). I'm not a total newb or anything but this is my kids' computer and I'm tired of dealing work wifi issues every other day but I also don't want to make it worse.
Is the wl driver available for you in System > Adminstration > Hardware Drivers?

---

### Post by enli on 2008-09-18
Hi.. I too managed to install wl driver.But strange thing is that wlan0 (was using ndiswrapper before wl) is renamed to eth1 and i cant scan the network.

[codfe]iwlist scan[/code]
says that none of the interfaces scan or something like that.

I see big improvement over the signal strength i can have with this driver. Previously with ndiswrapper : 14-16% now with wl :20%.
I dont want to configure eth1 manually as with ndiswrapper nm-applet could connect to the AP but with eth1 (wl driver) it gets confused i guess.

What would be the remedy ?

Regards
EnLi

---

### Post by cyberdork33 on 2008-09-18
did you make sure to unload / block ndiswrapper?

---

### Post by enli on 2008-09-18
> **cyberdork33 said:**
> did you make sure to unload / block ndiswrapper?

I am new to ubuntu so excuse my negligence on that topic.

ndiswrapper wasnt added to /etc/modules so i guess it was not loaded and i did a reboot before i updated kernel as the first post of the topic suggests.

How do i check if ndiswrapper wasnt loaded ?  
Is this right ?```
modprobe -l | grep ndiswrapper
```

Also i checked if wlan card was using the right driver by using
```
lshw -C network
``` module was "wl"

Regards
EnLi

---

### Post by m.musashi on 2008-09-21
> **cyberdork33 said:**
> Is the wl driver available for you in System > Adminstration > Hardware Drivers?

No. It isn't. Do I need to enable a different repo or install the referred to kernel?

---

### Post by cyberdork33 on 2008-09-21
> **m.musashi said:**
> This is certainly good news and something I've been hoping for. However, could someone explain the exact steps to take to get this working via the kernel update (without running the risks involved with the proposed repo). I'm not a total newb or anything but this is my kids' computer and I'm tired of dealing work wifi issues every other day but I also don't want to make it worse. 

Thanks.
Yes, in hardy it is in the proposed repo. If you look near the beginning of this thread (1st page), there is information about this. It might be easier to just wait a month or so for Intrepid as it will be included by default there.

---

### Post by m.musashi on 2008-09-22
Well, for better or worse, I enabled the hardy proposed repo and installed the new kernel. The wl driver then showed up as in use. It seemed a bit flaky so I did the below steps from page 1 and all seems to be working. I've had issues in the past with the connection just stopping working even though network manger showed it connected. We'll see if this solves that issue.

> **_mario_ said:**
> This yields the following /etc/modprobe.d/wl file:
```

# blacklist unwanted modules for wl to work
blacklist ssb
blacklist b43
blacklist b43legacy
blacklist ndiswrapper

# ignore symbols' versions (necessary on 2.6.24-21)
install wl /sbin/modprobe --ignore-install --force-modversion wl $CMDLINE_OPTS

```

Don't forget to run:
```

update-initramfs -k all -u

```

Someone also mentioned bypassing network manager and setting up the connection in network interfaces. Anyone try that? Just curious how it worked.

---

### Post by Ek0nomik on 2008-10-06
Has anyone gotten this working on Intrepid?  Intrepid includes wl, but loading the wl module doesn't bring on the WiFi light.

---

### Post by cyberdork33 on 2008-10-06
> **Ek0nomik said:**
> Has anyone gotten this working on Intrepid?  Intrepid includes wl, but loading the wl module doesn't bring on the WiFi light.
works for me... see the first few posts in this thread about disabling ssb...

---

### Post by Ek0nomik on 2008-10-06
> **cyberdork33 said:**
> works for me... see the first few posts in this thread about disabling ssb...

Edit:  Perhaps my altered state last night led to my different results.

Is there any way to keep the b44 module loaded and make use of wl?  My wired is a broadcom b44.

Edit2:  What's the easiest way to control module load order in Ubuntu?  Do I need to do a script to actually unload modules and put them in the right order, or is there a more efficient way of handling the load order from the initial startup?

---

### Post by cyberdork33 on 2008-10-07
> **Ek0nomik said:**
> Is there any way to keep the b44 module loaded and make use of wl?  My wired is a broadcom b44.Ah darn, I hadn't thought about the wired broadcom devices... I think it is OK, just a loading order that needs adjustment.

> **Ek0nomik said:**
> Edit2:  What's the easiest way to control module load order in Ubuntu?  Do I need to do a script to actually unload modules and put them in the right order, or is there a more efficient way of handling the load order from the initial startup?It may work if you put all the modules in the blacklist (ssb, b43, b43legacy, b44, wl) then add entries in /etc/modules in the order you like (and exclude modules such as b43 that you don't want). If that doesn't work, Creating the script to do it is probabaly the best option until this loading order problem is resolved.

---

### Post by hajk on 2008-10-10
Several people here have commented on the fact that the new "wl" driver results in the "eth1" interface, where they would prefer something like "wlan0" being more descriptive. This is easily fixed by editing the /etc/udev/rules.d/z25_persistent-net.rules file and changing "eth1" to "wlan0".

---

### Post by cyberdork33 on 2008-10-10
> **hajk said:**
> Several people here have commented on the fact that the new "wl" driver results in the "eth1" interface, where they would prefer something like "wlan0" being more descriptive. This is easily fixed by editing the /etc/udev/rules.d/z25_persistent-net.rules file and changing "eth1" to "wlan0".
They may have changed that recently too. I swear that it was creating wlan0 before...

---

### Post by Ek0nomik on 2008-10-10
I will get back to you on the module load order...

however, I can report that I am getting eth1 instead of wlan0.  Not that it really matters, but I will give the udev rule a look later on and post my results.

---

### Post by MaddMatt on 2008-10-21
I just switched to this driver in Hardy from the Hardware Drivers gui. 
It seems to be handling wireless better than ndiswrapper was, however, it has **now caused 4 hard crashes of the system** (well freezes, actually). 

At first I thought it was the ndiswrapper conflict, so I removed it from modprobe, and from /etc/modules and removed ndiswrapper from /etc/init.d and etcetera. But it's still crashing, and because my system tries to connect on log in, I was forced to disable it so that I can actually log in.... 

**Has anyone else had this problem?** I don't think this helps much, but here are some syslog entries... If there is a better logfile to investigate, please let me know, as I couldn't see much different in the others.

> Oct 21 15:09:53 Athens kernel: [   68.599207] CPU0 attaching NULL sched-domain.
Oct 21 15:09:53 Athens kernel: [   68.599213] CPU1 attaching NULL sched-domain.
Oct 21 15:09:53 Athens kernel: [   68.612493] CPU0 attaching sched-domain:
Oct 21 15:09:53 Athens kernel: [   68.612498]  domain 0: span 03
Oct 21 15:09:53 Athens kernel: [   68.612501]   groups: 01 02
Oct 21 15:09:53 Athens kernel: [   68.612505] CPU1 attaching sched-domain:
Oct 21 15:09:53 Athens kernel: [   68.612507]  domain 0: span 03
Oct 21 15:09:53 Athens kernel: [   68.612510]   groups: 02 01
Oct 21 15:09:54 Athens kernel: [   69.148949] eth1: no IPv6 routers present
Oct 21 15:09:58 Athens NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 21 15:10:11 Athens NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 21 15:10:11 Athens dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 21 15:10:11 Athens NetworkManager: <info>  Will activate connection 'eth1/Tabakoto 1'. 
Oct 21 15:10:11 Athens NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 21 15:10:11 Athens NetworkManager: <info>  Activation (eth1) started... 
Oct 21 15:10:11 Athens NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 21 15:10:11 Athens NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 21 15:10:11 Athens NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 21 15:10:11 Athens NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 21 15:10:11 Athens NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 21 15:10:11 Athens NetworkManager: <info>  Activation (eth1/wireless): access point 'Tabakoto 1' is unencrypted, no key needed. 
Oct 21 15:24:38 Athens syslogd 1.5.0#1ubuntu1: restart.


I mean, I could always go back to using just ndiswrapper, but I got better signal strength out of this driver, actually. (or so the little bars tell me...) so I'd like to give it a show. 

PS - note that it's still 'eth1'... I doubt that is an issue, but I might change that just to see. 

Let me know if you guys have any ideas! Thanks, 
M

---

### Post by _mario_ on 2008-10-21
> **MaddMatt said:**
> 
It seems to be handling wireless better than ndiswrapper was, however, it has **now caused 4 hard crashes of the system** (well freezes, actually). Has anyone else had this problem?

yes. the machine is always freezing right after connecting to a WPA2-Enterprise secured network (both Hardy & Intrepid). in this case nsdiwrapper works better, but (in general) has worse link quality. that's exactly what you observed. and there is still no updated version on broadcom's web site ...

the only "solution" so far: blacklist both ndiswrapper and wl and load the module to be used manually (usually ndiswrapper but sometimes wl is really necessary).

> **MaddMatt said:**
> 
PS - note that it's still 'eth1'... I doubt that is an issue, but I might change that just to see. 


that didn't cause the crash.

ciao,
Mario

---

### Post by MaddMatt on 2008-10-22
Yeah, I think I'll stick with ndiswrapper until this is fixed. Note, though that I'm connecting to an unsecured network (*gasp!* those still exist?). But keeping my computer stable is more important to me than preformance at this point. 

Thanks for the info!
M

---

### Post by maximilianhauser on 2008-11-06
Hello!
Since i installed the Broadcom STA driver, the network manager wicd doesn't work anymore. Does anyone other have this problem? Wicd shows the network, but i can't access to it. A connection with wpa_supplicant is no problem.

---

### Post by AleXit on 2008-11-06
> **maximilianhauser said:**
> Hello!
Since i installed the Broadcom STA driver, the network manager wicd doesn't work anymore. Does anyone other have this problem? Wicd shows the network, but i can't access to it. A connection with wpa_supplicant is no problem.

Yes, I confirm that.
With Network Manager 0.7 there are no problems.

I think is something related to permissions... but we need to investigate better wicd logs.

Moreover (I dont know if it's realated to Wicd problem) I noticed that "iwconfig" shows its results only if it is executed as root. Anyone could confirm that? And how we could solve that?:confused:

---

### Post by dark_harmonics on 2008-11-19
Using the broadcom sta driver (macbook pro) my computer exhibits your freezing issue with an enterprise WPA network (at my work). Very annoying to have no wireless at work! Is there any way for me to get this working with the new driver? Performance is an issue in my instance because i transmit large files (image files) back and forth between servers.

---

### Post by coolguykris on 2008-12-10
ok so I am stuck on installing this... I have read the read me ([http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)) and am stuck on step number 4 and 5. I changed the 2.6.xx.xx to the proper number but it says it can not find the file. There is no modules/5.10.27.6/build folder in my lib folder. I am completely dumb when it comes to ubuntu so I know I am just missing something easy. Any help?

---

### Post by coolguykris on 2008-12-10
Here is what I have been trying to do... in the number section I have aslo tried the version of the driver too and that didn't work. What am I doing wong? > kris@ubuntu:~$ cd hybrid_wl 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/2.6.27/build M='pwd' clean 
make: *** /lib/modules/2.6.27/build: No such file or directory.  Stop. 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/2.6.27.9/build M='pwd' clean 
make: *** /lib/modules/2.6.27.9/build: No such file or directory.  Stop. 
kris@ubuntu:~/hybrid_wl$ /lib/modules/2.6.27-9/build M='pwd' 
bash: /lib/modules/2.6.27-9/build: No such file or directory 
kris@ubuntu:~/hybrid_wl$ /lib/modules/2.6.xx.xx/build M='pwd' 
bash: /lib/modules/2.6.xx.xx/build: No such file or directory 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/2.6.xx.xx/build M='pwd' clean 
make: *** /lib/modules/2.6.xx.xx/build: No such file or directory.  Stop. 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/2.6.27/build M='pwd' clean 
make: *** /lib/modules/2.6.27/build: No such file or directory.  Stop. 
kris@ubuntu:~/hybrid_wl$ 
kris@ubuntu:~/hybrid_wl$  make -C /lib/modules/<2.6.27>/build M='pwd' clean 
bash: 2.6.27: No such file or directory 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/<2.6.27-9>/build M='pwd' clean 
bash: 2.6.27-9: No such file or directory 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/<2.6.27.9>/build M='pwd' clean 
bash: 2.6.27.9: No such file or directory 
kris@ubuntu:~/hybrid_wl$ 


---

### Post by _mario_ on 2008-12-10
> **coolguykris said:**
> ok so I am stuck on installing this... I have read the read me ([http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)) and am stuck on step number 4 and 5. I changed the 2.6.xx.xx to the proper number but it says it can not find the file. There is no modules/5.10.27.6/build folder in my lib folder. I am completely dumb when it comes to ubuntu so I know I am just missing something easy. Any help?
what about using the pre-compiled version found in the linux-restricted-modules-generic package?

ciao,
Mario

---

### Post by coolguykris on 2008-12-10
I was having too many problems with it, like so many around here.

---

### Post by _mario_ on 2008-12-10
> **coolguykris said:**
> I was having too many problems with it, like so many around here.
sorry, i missed your second-last post...

> **coolguykris said:**
> kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/2.6.27/build M='pwd' clean
these commands are seriously broken:
[LIST=1]
[*]it should be: M=`pwd` (note backticks!). you might be better off using M=$PWD instead.
[*]the version mentioned must match the installed kernel version. have a look at the directory /lib/modules/. usually it's something like 2.6.27-8-generic. the -C option refers to the kernel version the module is to be compiled against (well, in fact a link inside its installation directory).
[*]additionally, you'll need to install the kernel headers first (package linux-headers-generic).
[/LIST]

so the line should look like this:
```
make -C /lib/modules/`uname -r`/build M=$PWD clean
```
to compile against the running kernel (again `uname -r` is enclosed in backticks).

however, since the version shipped in Ubuntu's restricted drivers package is the same as the one available from the broadcom site, you won't have much luck compiling the driver yourself, if the pre-compiled one doesn't work.

ciao,
Mario

---

### Post by coolguykris on 2008-12-10
I got this
> kris@ubuntu:~$ cd hybrid_wl 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/`uname -r`/build M=$PWD clean 
make: Entering directory `/usr/src/linux-headers-2.6.27-9-generic' 
make: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic' 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/`uname -r`/build M=$PWD clean 
make: Entering directory `/usr/src/linux-headers-2.6.27-9-generic' 
make: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic' 
kris@ubuntu:~/hybrid_wl$ make -C /lib/modules/`uname -r`/build M=$PWD 
make: Entering directory `/usr/src/linux-headers-2.6.27-9-generic' 
  LD      /home/kris/hybrid_wl/built-in.o 
  CC [M]  /home/kris/hybrid_wl/src/wl/sys/wl_linux.o 
  CC [M]  /home/kris/hybrid_wl/src/wl/sys/wl_iw.o 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c: In function &#8216;wl_iw_get_scan&#8217;: 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:934: error: too few arguments to function &#8216;iwe_stream_add_event&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:939: error: too few arguments to function &#8216;iwe_stream_add_point&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:947: error: too few arguments to function &#8216;iwe_stream_add_event&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:955: error: too few arguments to function &#8216;iwe_stream_add_event&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:961: error: too few arguments to function &#8216;iwe_stream_add_event&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:973: error: too few arguments to function &#8216;iwe_stream_add_point&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:981: error: too few arguments to function &#8216;iwe_stream_add_point&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:992: error: too few arguments to function &#8216;iwe_stream_add_point&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1006: error: too few arguments to function &#8216;iwe_stream_add_point&#8217; 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast 
/home/kris/hybrid_wl/src/wl/sys/wl_iw.c:1016: error: too few arguments to function &#8216;iwe_stream_add_value&#8217; 
make[1]: *** [/home/kris/hybrid_wl/src/wl/sys/wl_iw.o] Error 1 
make: *** [_module_/home/kris/hybrid_wl] Error 2 
make: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic' 




That doesn't seem liked it worked. What was wrong with it?

---

### Post by _mario_ on 2008-12-11
> **coolguykris said:**
> I got this
That doesn't seem liked it worked. What was wrong with it?
the function iwe_stream_add_value in recent kernel versions seems to require 6 arguments (defined in include/net/iw_handler.h:569), while the driver code tries to pass only 5. according to the broadcom site the code if fairly outdated, so you'll have to fix it before compiling.
... or use Ubuntu's pre-compiled version ...

did you read the last paragraph of my previous post?

ciao,
Mario

---

### Post by Ryian on 2009-01-03
Just want to share with you guys my set up and works with the new Ubuntu 8.10 the Intrepid Ibex released in October 2000 for MacBook Pro (w/ Core2  Duo 15 inch) with Broadcom 4328 (rev 5). I don't have to do anything about hacking driver at all. The Interepid Ibex comes with Braodcom STA wireless driver in the "Restricted drivers". You just have to "activate" it.

Step-1: (See what WiFi chipset you have)
$lspci:
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)

Step-2: "Activate" Broadcom BCM4328 WiFi driver
Menu -> System -> Administration -> "Hardware Drivers"

You will see a list of proprietary drivers like,
  - NVIDIA, Broadcom STA

Just select the radio button for "Broadcom STA wireless driver" and then
click the "Activate" button at the lower right corner. It will take minutes to complete. (Note. I also activate the "NVIDIA graphics driver version 177 as marked Recommended)

I just reboot MacBook to be certain. After reboot, I just use the following steps to add WiFi connection:

Steps:

  System -> Preferences -> Network Configuration (a NetworkManagent 
  gui will popup)
   
  Click "Wireless" Tab folder and then "Add".
  
  For me, I use "Infrastructure" mode and choose your own mode.
  
An warning to share with you is that the STA driver in this (my) 
MacBook Pro requires the Wireless Router to "broadcast" its SSID.
I tried three times to turn off and then Broadcom driver can not
pass through the "security" login onto the Wireless Router. Once
I made the SSID broadcast (I don't like to show my SSID to my
neighbors or intruders), the MacBook Pro with Ubuntu has no problem in 
establishing connection. -- So, I suspect that some bug in STA driver
working with MacBook Pro. When I switch to MacOS boot up, and it
has no problem at all for access the hidden SSID. So, it indicates
that some minor bug of MacBook Pro in interfacing with STA driver
during initial authentication requiring broadcast SSID mode. That's
maybe why many reports about the "security encryption" not working.
Also, if you could try to use the WPA/WPA2 without Auto mode in your
Wireless Router (e.g., my D-Link)

Good luck for using BRCM 4328 WiFi for your Ubuntu with your 
MacBook Pro. :-)

 -R

---

