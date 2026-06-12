---
title: "PowerMac G5 Wifi Issues"
date: 2012-08-26
forum: Apple Hardware Users
---

### Post by rprescott11 on 2012-08-26
Hi Everyone,

I thought I would ask for help after I have tried to get wifi to work on my G5 this whole week. I have the following network card installed:

0001:06:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
	Subsystem: Askey Computer Corp. Sonnet Aria Extreme PCI
	Flags: bus master, fast devsel, latency 16, IRQ 53
	Memory at 90000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

I have b43legacy module loaded in /etc/modules and blacklist the following:
blacklist snd-powermac
blacklist wl
blacklist ndiswrapper
blacklist bcm43xx

I havent yet tried to configure an access point as I cannot even scan to see a list of them which is making me believe its a driver issue.

Here is the output of dmesg | grep -i b43

[    3.464819] b43-pci-bridge 0001:06:03.0: enabling device (0004 -> 0006)
[   16.484037] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   16.505632] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   16.505655] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   16.529402] b43legacy-phy0 debug: Radio initialized
[   18.537423] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   18.605952] b43legacy-phy0 debug: Chip initialized
[   18.606009] b43-pci-bridge 0001:06:03.0: Warning: IOMMU window too big for device mask
[   18.606014] b43-pci-bridge 0001:06:03.0: mask: 0x3fffffff, table end: 0x80000000
[   18.606019] b43legacy-phy0 ERROR: The machine/kernel does not support the required 30-bit DMA mask
[   18.606292] b43legacy-phy0 warning: DMA for this device not supported. Falling back to PIO
[   18.606339] b43legacy-phy0 debug: PIO initialized
[   18.606602] Registered led device: b43legacy-phy0::tx
[   18.606643] Registered led device: b43legacy-phy0::rx
[   18.606678] Registered led device: b43legacy-phy0::radio
[   18.606746] b43legacy-phy0 debug: Wireless interface started
[   18.606771] b43legacy-phy0 debug: Adding Interface type 2

Any advice?  Maybe I am using the wrong module?  I see some errors in dmesg that worry me a little. Oh btw I have the latest ubuntu 12.04 PPC with all updates downloaded.

---

### Post by 2blue on 2012-08-26
What does legacy module mean? I have an iBook G4 from 2005, wireless lists as Broadcom BCM4318 (Air Force One 54G)  802.11g.  It works fine

Here is my terminal output: 

:~$ dmesg | grep -i b43
[   12.370684] Registered led device: b43-phy0::tx
[   12.370872] Registered led device: b43-phy0::rx
[   12.371024] Registered led device: b43-phy0::radio
[   22.575877] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[ 7966.111693] b43-pci-bridge 0001:10:12.0: restoring config space at offset 0x4 (was 0x0, writing 0x80084000)
[ 7966.111701] b43-pci-bridge 0001:10:12.0: restoring config space at offset 0x3 (was 0x0, writing 0x1000)
[ 7966.111710] b43-pci-bridge 0001:10:12.0: restoring config space at offset 0x1 (was 0x0, writing 0x6)
[ 7971.842465] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)


Edit. I see you have correctly installed legacy packages according to [this]("http://linuxwireless.org/en/users/Drivers/b43") page.  You might get support on the irc channel listed. Unless the wireless module is uncorrectly detected, I`m not sure why it doesn`t activate. 

This is the line you have ran in terminal?  sudo apt-get install firmware-b43-installer

---

### Post by rprescott11 on 2012-08-26
I ran the following command to install:
sudo apt-get install firmware-b43legacy-installer

I tried to activate the b43 driver using additional drivers (jockey) and it crashed both the gtk and text versions. I think its a bug in jockey: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/969255](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/969255)

Maybe that's my issue how do I activate it without jockey?

---

### Post by 2blue on 2012-08-26
There is the list of stuff to go through on the [FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#Drivers_and_Hardware") page. 

Card might need something simple like tagging of for activation, or if all fails (which it should not) perhaps installing a completely different make of drivers.

---

### Post by rprescott11 on 2012-08-26
Sorry to sound dumb but what kind of tagging? I did follow all the steps and suggestions on that FAQ with no go.  This is my second full reinstall of the system.

---

### Post by 2blue on 2012-08-26
Perhaps it`s "tick of" or "mark of"? My English could be better. I`m not sure how it is in Unity, but if you log on in gnome, there should be an upper (?) launch panel with the wireless icon. Can you double finger klick your mouse on the icon, and see if it is enabeled? It`s sometimes simple things that makes things difficult, but with a bit of luck it is easily sorted out. It should say something like "enable wireless" and "enable networking".

Edit: I think the launch bar in Unity is all regular with functions, so you don`t have to logon in gnome. Sorry have haven`t used Ubuntu much after Unity was introduced.

---

### Post by rprescott11 on 2012-08-26
Yes enable networking and enable wireless is checked.  I think more now that it has to do with the linux kernel and module not be compatible with DMA which is an error I get in the dmesg.

---

### Post by 2blue on 2012-08-26
I noticed there is a [support irc channel]("http://linuxwireless.org/en/users/Drivers/b43/") on freenode; #bcm-users. There are some clever guys posting here like rsavage and others, maybe they will read your post sooner or later.

---

### Post by rsavage on 2012-08-27
Like 2blue says I would start by toggling the "Enable Wireless"/"Enable Networking" options.  I had to turn one of them off then turn it back on again before I started seeing networks (can't remember which one now).  Network Manager is not good in 12.04 (I've now ditched it).  Have you tried scanning networks from the command line?

The error in your dmesg may not be anything to worry about.  It says it is falling back to PIO (whatever that means).  I am not a network expert at all.

Random google search brought this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951687](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951687) .  Looks different to yours though (they don't have a legacy card).  Also a patch [http://comments.gmane.org/gmane.linux.kernel/1345564](http://comments.gmane.org/gmane.linux.kernel/1345564) .

Have you tried using a kernel from a previous version of ubuntu to see if it is kernel related?  Have you previously had it working in linux?

---

### Post by rprescott11 on 2012-08-27
This is my first time installing Linux on my G5 PPC.  I tried running a scan from the command line but with no results.  Which I should have a bunch of networks.  I think that patch might work for me as I have more than 1gb of ram.  How do I apply that patch or a newer kernel?  Thanks for your help!

---

### Post by rsavage on 2012-08-28
I'm afraid you'll have to investigate compiling kernels yourself.  It has been ages since I've done that sort of thing.  What I would do if I was in your position would be to link that patch to the launchpad bug report and see if you can get the ubuntu kernel people interested in it.

Installing a pre-built kernel is easy.  For example, the latest oneiric one lives here [https://launchpad.net/~canonical-kernel-team/+archive/ppa/+build/3722101](https://launchpad.net/~canonical-kernel-team/+archive/ppa/+build/3722101)

Download the linux-image-3.0.0-25-powerpc64-smp_3.0.0-25.41_powerpc.deb file and then run the command 

sudo dpkg -i  linux-image-3.0.0-25-powerpc64-smp_3.0.0-25.41_powerpc.deb

You may have to install the wireless-crda package first.

Reboot

Follow the links here to get the latest quantal (development) kernel [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux) 

I have not heard of this problem before so I think it must be new?

Try a 10.04 live cd.  Copy the /lib/firmware/b43legacy directory from your installed system to the same location when running the live cd.  You will then get wireless.  Or you can run
sudo apt-get install b43-fwcutter

---

### Post by rprescott11 on 2012-09-06
I found out a SOLUTION was to downgrade to 10.04 and everything worked sound/wifi!!

---

