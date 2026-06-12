---
title: "CPU usage problem"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Reshuken on 2007-09-09
Hello guys. Yesterday while I was surfing the net, I got some serious lag on my computer. I don't know if it's related, but it went as far as fading my screen to a "black and white" mode (I don't know if someone understands what I mean... sometimes I get that same effect when installing packages from Synaptic). 
In any case, I don't know what was causing it, but I checked my system monitor to see if anything seemed wrong. Although I am new to Linux and all, I can tell for sure that my CPU usage was between 5-6% last time I checked, without any program open, but now its always between 8-12% and I don't have anything running. Someone can explain me what could be causing this abnormal CPU use? And how could I solve this? Thanks in advance.

---

### Post by st33med on 2007-09-09
Hello. what is your Video card? To find out, do:
```
lspci
```
and post it here.

As for the processes, that should be normal, it could be anything from networking to a video card problem.

---

### Post by Reshuken on 2007-09-09
It's an ATI Mobility Radeon 9000. I'm on a Dell Laptop, a Latitude D600 if that helps.

The output of lspci is:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by st33med on 2007-09-09
Yeesh. ATI is a headache. Follow this link.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Reshuken on 2007-09-09
Hmmmm, about being a video card problem, I don't think it's that. In my first post, I didn't mention that I have Beryl and the appropiate video drivers. Well, actually I followed what is said on this page:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
As far as I can remember, the CPU usage was below 6% after I followed that guide, and it was like that until yesterday. This is something recent, I can't figure out what could be wrong. Any other advice?

---

### Post by shae on 2007-09-09
could you just be forgetting that your cpu throttles down when idle?

---

### Post by Reshuken on 2007-09-09
Of course I know that my CPU just slows down when I'm not doing anything. What I'm saying is that it used less power before.
Anyway, I went to the terminal and used the top command. and it seems like the CPU usage is kind of normal: xorg uses around 6% and everything else is pretty much idle. 
BUT, once in a while I found a couple processes that jumped for about a second and then disappeared: one is a command "hald" and the user is "haldaemo" and the other is something cupsys or the like (It flashes real fast and I can't exactly read it).
My question is, what kind of processes are those? I didn't expect to see anything besides my user and root.

---

### Post by Harpoon on 2007-09-09
hal is related to hardware devices (like enabling you to hotplug a usb disk).  cups is used tofor printing and printers.  Neither is a problem.  I'm betting beryl will intermitently suck up cpu, but that is only a guess.

---

