---
title: "Help Needed Establishing Wired Connection to Internet"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by clevelandohio on 2007-02-20
UPDATE: Okay, in the few moments that passed since I posted this message, I've located the problem: ME!

In my haste to install the ethernet card, I merely plugged in the cables as they had been plugged into the previous card -- which only had a dial-up modem.

So, I had not plugged in the ethernet portion of the card. I actually found the solution by searching this forum. I was so set on identifying a software issue or other hardware issue, I never considered the obvious! Some one out there had made the same mistake as I.

So, problem solved. Always check to make sure you have the ethernet card correctly plugged into the mother board.



==========================
I'm trying to establish a wired Internet connection, but I'm a total Ubuntu noob. So, please, any help you can provide will be very much appreciated. I'm determined to get this to work, and I need your assistance. 

I'm using Ubuntu 6.10 Edgy Eft on a Dell Inspiron 2500.
The ethernet card is a 3com 3C556 (see lspci details below)

I subscribe to SBC Yahoo (AT&T) DSL. I'm using a Speedstream 5100 Ethernet ADSL Modem that is connect to a Linksys WRT54G Broadband Wireless router. The router is connect to my laptop via a cable. To be clear, I'm trying to establish a wired Internet connection. I do not have a static IP address. It is dynamic.

When I click on "Network Settings", "Wired Connection, Address:DHCP" is visible.
I clicked on it and selected the "Enable this connection" button. The configuration selection box says: "Automatic Configuration (DHCP).
  

I am not able to access the Internet at all. This is my stumbling point. I don't know what do next. I've spent several hours searching these forums, but haven't found any solutions specific to my problem.

I've even tried connecting the modem directly to the laptop -- thinking maybe the router was causing a problem, but it didn't solve the problem. 

If anyone can offer any advice, I'd really appreciate it!

Thank you!


Here is what the lspci command returned:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 03)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:0b.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
01:0b.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)

---

### Post by n8bounds on 2007-02-20
Nice troubleshooting in any case!

---

### Post by tgalati4 on 2007-02-21
Like I said, Cleveland rocks!  Good job with posting the troubleshooting info.  If only we can get more people to post basic information, it makes troubleshooting so much easier.

---

### Post by irish_flu on 2007-02-21
> **clevelandohio said:**
> UPDATE: Okay, in the few moments that passed since I posted this message, I've located the problem: ME!

In my haste to install the ethernet card, I merely plugged in the cables as they had been plugged into the previous card -- which only had a dial-up modem.

So, I had not plugged in the ethernet portion of the card. I actually found the solution by searching this forum. I was so set on identifying a software issue or other hardware issue, I never considered the obvious! Some one out there had made the same mistake as I.

So, problem solved. Always check to make sure you have the ethernet card correctly plugged into the mother board.


I'll only tell this story because we're all friends here, but if it makes you feel better:

For a decade now, I've been a professional user support guy, hardware tech, and now a sysadmin.

Last time I built a new PC for myself, I was excited because I'd been using the same rig for a long time.  I bought all the parts at NewEgg, and they all showed up on the same day except or the video card.

Well, I wanted to put it all together anyway and make sure nothing was dead.  I carefully put together the entire machine and fired it up, expecting to hear a "no video card" beep code from the motherboard.

Hit the power button, and NOTHING.  Crap, oh no, I've screwed something up or one of my parts is DOA.  

Looked inside the case, made sure everything looked right, etc.  Everything looked cool.  I was fairly ticked off.

It was several minutes before I noticed there was no power cord....

---

### Post by n8bounds on 2007-02-21
LOL, good stuff

---

