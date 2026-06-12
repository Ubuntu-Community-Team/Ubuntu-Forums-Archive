---
title: "distorted screen when starting ubuntu"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-06-10
How come whenever I start ubuntu the screen will go haywire before going to the login screen, and it'll do the same when loging out and shitting down. By haywire I mean it looks like it's glitching.

It doesn't really effect performance, it just looks unprofessional and rediculous:(

---

### Post by w4ett on 2007-06-10
Sounds like a problem with your xorg.conf and/or video drivers.....post the results of lspci and your xorg.conf file for us

---

### Post by LostArt on 2007-06-10
I can't get on my ubuntu computer right now, but do you think it's because I have an ATI card??

---

### Post by w4ett on 2007-06-10
It's a possibility.....ATI (I'm using an ATI 9200 card) can be a bit of a pain in the &*%$ to set up sometimes.....they have LOUSY Linux support.  I had a similar problem when I was using the onboard vid on my motherboard (SIS 741) .  When you have a chance...post those files and let's see what can be done.

---

### Post by Jimmyfj on 2007-06-10
Hi 

I have been installing a number of computers with a ATI graphics card - The only way they seem to be able to install Ubuntu is by using the Ubuntu alternate-install-cd instead of the usual live-cd.

I have yet to find a way to get around the problem you mention. The maschines I've installed was destined to be converted fully to Ubuntu thus not run a dual-boot configuration.

---

### Post by shamushand on 2007-06-10
I sadly have the same experience with distorted screens at startup on an old i810 card. I'm sure it has something to do with the card and xserver, firstly because installation kust crashes unless with alternate CD, and because when I broke X (completely) all I got was the distorted flashing screen, and it wouldn't load. I'm also looking for the solution to this problem, it's kind of annoying. ;)

---

### Post by LostArt on 2007-06-10
here's lspci

00:00.0 Host bridge: ATI Technologies Inc Unknown device 7831
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 9200 IGP
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)


and I don't remember how to view my xorg.conf err sorry if that sounds dumb but can someone post the command

---

### Post by w4ett on 2007-06-10
The command is: sudo gedit /etc/X11/xorg.conf  just copy and paste it into your post.

---

