---
title: "Cannot boot into Windows with Ubuntu dual boot"
date: 2013-04-12
forum: Any Other OS
---

### Post by JC Ignarus on 2013-04-12
Hey guys, I have Ubuntu 12.04 installed and dual booting with Windows 7 Ultimate. I think someone must have hibernated or done something odd when they shut down Windows last, since whenever I try to open it now it freezes in the midst of starting and reboots the computer. If i try to access it again it launches startup repair, which yeilds these results among others:

Problem Event Name:            StartupRepairOffline
Problem Signature 01:            6.1.7600.16385
Problem Signature 02:            6.1.7600.16385
Problem Signature 03:            unknown
Problem Signature 04:            21199928
Problem Signature 05:            AutoFailover
Problem Signature 06:            7
Problem Signature 07:            NoRootCause
OS Version:                            6.1.7601.2.1.0.256.1
Locale ID:                              1033
 The Diagnosis and repair details for the most recent session read:
 Startup repair diagnosis and repair log
----------------------
Last successful boot time 1/23/2013 9:21:48 Pm (GMT)
Number of repair attempts: 7

I don't know whether any of you can make heads or tails of those numbers and words, though I certainly can't. I would really prefer not reinstalling the whole thing and going through that hell since I have some large games installed in Windows (Starcraft II, GTA IV, Human Revolution...) and it would be a real drag to have to reinstall Windows and those games. I posted this problem on a Windows forum, and the response was useless. Hope you guys have something to suggest and if you need more info please ask. Thanks

---

### Post by cody1233 on 2013-04-12
Welcome to the forum!

It sounds to me like Windows rewrote your boot record or something so what I would do is go online and download a GRUB Rescue Disk.  From there, write it to a CD and pop it into the computer that's messed up.  Once it's booted onto that just start your Ubuntu OS and type "sudo update-grub" in a terminal.  If that STILL doesn't work, just try to reinstall GRUB...

Good luck!

---

### Post by JC Ignarus on 2013-04-14
Thanks for the reply, but perhaps I wasn't clear enough. I can access GRUB without a problem. I can select Ubuntu and Windows from the GRUB screen when I boot up, but the problem is when I try booting into Windows. If I select Windows from the GRUB menu, Windows starts to boot, but stops at a certain point (the four colored orbs if you've ever used 7), and reboots the computer. If I try to boot into Windows again after the reboot, it brings me to WIndows' "system repair" which is never actually able to fix the problem. I think I once read that Windows sometimes has hibernation issues when dual booting, and I'm wondering if that might have anything to do with it...

---

### Post by cody1233 on 2013-04-16
Ohhhh...that might, but i'm DEFINATELY not an expert in Win booting...sorry!

---

