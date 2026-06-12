---
title: "[SOLVED] Ethernet Issues"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by TheGreatSage on 2007-07-14
Hi there

I have recently installed Ubuntu (dual boot with xp on a new machine) . I have been having problems getting a network connection and pinging my router.After messing around for ages, I finally realised that the network port is not lighting up on the router or on my pc.

It works fine with Xp, so I am guessing it may be a driver issue. I have looked on my chipset driver disc and there is a linux driver, but I have no idea how to install it.

Does anyone have any suggestions?


Thanks
J

---

### Post by w4ett on 2007-07-14
Ok, we're going to need some further info.  In your terminal type:  lspci

the output of this command will give us the controller chipsets for your system and this will give us the ethernet chipset that is on your M/B or card.

---

### Post by TheGreatSage on 2007-07-14
0:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1c.5 PCI bridge: Intel Corporation Unknown device 294a (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0421 (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
**04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01**)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Thanks!

---

### Post by w4ett on 2007-07-14
Gigabit controller...Hmmmmmm. I think I read it's not been implemented in the current kernel...

Let me check and I'll be back

---

### Post by w4ett on 2007-07-14
There appear to be some issues:  

[http://ubuntuforums.org/showthread.php?t=437982&highlight=RTL8111%2F8168B+PCI+Express+Gigabit+Ethernet+controller](http://ubuntuforums.org/showthread.php?t=437982&highlight=RTL8111%2F8168B+PCI+Express+Gigabit+Ethernet+controller)

---

### Post by TheGreatSage on 2007-07-14
s of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.


Used the above information from the thread you linked and I'm now logged into the forum with Ubuntu.

Thanks a lot for your help, I was pulling my hair out. =D>

---

### Post by w4ett on 2007-07-14
I knew I had read something about it here in the forums...Glad to have helped....Good Luck!

---

### Post by spacetom81 on 2007-07-16
I had Ubuntu 7.04 installed on my E1505 not too long ago and it was working well, I followed all the tutorials out there about how to get my ATI graphics card drivers to work and how to get the wireless internet to work, but when I ran the updates it screwed up everything i had worked on and the connection to any network, wireless or wired ceased to work. I've re-installed 6.10 (which i updated to 7.4 from last time) but this install i'm still having stupid problems with the ethernet. obviously i can't install updates or do much of anything without a connection to the internet on my laptop so i'm kinda stuck at a stand-still. i've done everything that's supposed to be done in order for the internet to work but it's not even registering that the computer is hooked to the ethernet. When I plug the ethernet cable in, the lights on the back of my computer cut on and it says i've established a connection, and in network manager i can see that i'm recieving information. I'm not even going through the router at this point it's just plugged straight into the modem and it's still not connecting to anything. The ethernet adapter is a Broadcom BCM4401-B0.

any help would be appreciated. :(

---

