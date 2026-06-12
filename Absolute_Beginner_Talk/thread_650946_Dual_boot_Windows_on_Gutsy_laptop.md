---
title: "Dual boot Windows on Gutsy laptop"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Want A Pie on 2007-12-27
Hi, I have Gutsy Gibbon installed on my laptop, but I want to install Windows XP as well for Visual Basic .NET and iTunes.
I know how to do it if I start with Windows, but not if I start with Gutsy, so if there is a way that I can remove Gutsy, then install XP and recover my Gutsy, (I don't want to set it up again or download the 200 and something updates)

I hope someone can help, but please only tell me the easiest option, and tell me how to do that option, not a list of many :D

Thanks in advance

---

### Post by chewearn on 2007-12-27
> **Want A Pie said:**
> Hi, I have Gutsy Gibbon installed on my laptop, but I want to install Windows XP as well for Visual Basic .NET and iTunes.
I know how to do it if I start with Windows, but not if I start with Gutsy, so if there is a way that I can remove Gutsy, then install XP and recover my Gutsy, (I don't want to set it up again or download the 200 and something updates)

I hope someone can help, but please only tell me the easiest option, and tell me how to do that option, not a list of many :D

Thanks in advance

General steps required:
1. Resize Gutsy to make way for XP (can use Ubuntu LiveCD, or GParted LiveCD)
2. Back-up Gutsy  partition (can use Ubuntu LiveCD, or GParted LiveCD)
3. Install XP into the freed area
4. Restore grub
manually: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
supergrub: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Want A Pie on 2007-12-27
OK, can you tell me what I do with steps 1 and 2? Do I reboot my computer and run from CD or insert the CD while running Gutsy?

---

### Post by chewearn on 2007-12-27
You reboot and run from the CD.  There, you will find the gparted program
(top menu > System > Administration > Partition Editor)

This will let you do step 1 and 2.  Note that, the program will probably crash each time it completes an operation (bug was fixed recently, but the LiveCD has an older version).  Don't worry about that, just restart the program again, and continue.

---

### Post by Want A Pie on 2007-12-27
ok, thanks, will try now

---

