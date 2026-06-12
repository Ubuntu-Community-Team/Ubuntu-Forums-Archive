---
title: "Uninstalling Ubuntu Linux"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by suds on 2005-11-29
I loaded Ubuntu Linux into my old Toshiba Tecra 8000 Laptop and messed around with it some. I wanted to see how it worked. I made a little progress with it, but not much.

Then my 86-year-old mom decided she wanted to learn to use a computer. This laptop was available, so I decided to give it to her. Since I am absolutely new to Linux, it made sense to me to restore the laptop to Win98 (since I can then help her more). So I used my disk image program (Power Quest Drive Image) to put the old Win98 system image back on the drive. This of course required repartitioning and reformatting and so on. None of which was a problem.

The problem is that when I reboot, I get seomthing called a grub error. This grub thing seems to be a remnant of the Linux system. It seem to occur before Win98 loads, and so I looked in the BIOS to see if it was calling out anything but no, it is not.

Here's the message: 

GRUB Loading stage1.5.
GRUB loading, please wait...
Error 17

How can I get rid of this grub, whatever it is, and allow Win98 to start up?

Thanks very much!

---

### Post by crazyness003 on 2005-11-29
My friend, im not very good at thems-kinds of things, but an easy solution that I would do is to do a **low-level format** on the drive. This should erase EVERYTHING, even your tables and records...and hopefully your Grub problem. I thikn you need special software to do it tho. Then do a high level format to regain the CHS, and then partition (or however the process goes). Do some more reserach on it tho; like i said, i'm not an expert. I just wanna direct you a little.

If i'm mistaken please, someone, correct me. I dont wanna be the cause of a major catastrophie.

Good luck man!

---

### Post by teaker1s on 2005-11-29
need to use fdisk to fix mbr

---

### Post by Hilgo on 2005-11-29
use your win98 bootfloppydisk (if you don't have one you can get it from bootdisk.com) and boot the laptop with it.
Then use fdisk /mbr and things should be fine afterwards.

---

### Post by suds on 2005-11-29
**fdisk /mbr** did the trick!  

Many thanks! From me and my old mom.

---

### Post by Brunellus on 2005-11-29
hope you visit her often to clean the (spy,ad)ware off her computer.

---

### Post by somody on 2005-11-29
That's what I would have reccommended (sp?) as well.

---

