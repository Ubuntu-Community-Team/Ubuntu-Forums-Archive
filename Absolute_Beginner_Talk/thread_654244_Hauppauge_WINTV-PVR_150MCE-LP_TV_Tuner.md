---
title: "Hauppauge WINTV-PVR 150MCE-LP TV Tuner"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by tjkick on 2007-12-30
I have a MythBuntu 7.10, an ASUS M2NPV-VM AM2 NVIDIA GeForce 6150 Micro ATX AMD Motherboard and two Hauppauge WINTV-PVR 150MCE-LP TV Tuner cards.  The operating system recognizes both cards and can record with each one, however MythTV repeatedly says "Failed to open card"  I've seen a lot of posts about the PVR 150, but not the 150MCE version.  Can anyone tell me what the problem might be and how to fix it?  I am brand new to Linux, Ubuntu and MythTV.  If anyone can help, I would really appreciate it.

---

### Post by georider on 2007-12-31
Ok, so your card works fine but mythtv repeatedly says it cannot open the card even though it does, yes? How is the warning displayed: in a terminal, log, pop up window? Is it possible some other process is trying to access the card?

I looked around a bit and found the MCE is for "Media Center Edition" but I could not find any definitive information on what is different on the card than a standard PVR-150.

LP is apparently "Low Profile".

---

### Post by despidey on 2007-12-31
Apparently Happaugue has occasionally substituted the PVR 150 with the 1600, which mythtv does not like.  
[http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-150](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-150) 
Make sure card is really a 150 before knocking yourself out any further   

BTW my understanding is that the MCE edition means that there is no remote or remote receiver included.

---

