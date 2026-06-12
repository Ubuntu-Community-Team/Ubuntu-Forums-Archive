---
title: "Fat32 USB HDD Not automounting"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by svelectric on 2007-03-27
I've worked on this issue for the last 2 hours and can't seem to get my new ubuntu system (6.10) to see my usb hard drive.  It is formatted with Fat32.  I installed gparted and it is not listed.  It seems to turn on fine, the green light is on the enclosure, etc.  Any chance of getting some help?  Thanks so much.

sv

---

### Post by Scarlett on 2007-03-28
I'm really new at this too, so take all advice with a grain of salt... and remember, if you break it you get to keep both pieces.  :wink: 

This is the walk-through that worked to get my internal drive mounted.  Should be almost the same except change ntfs to fat32 and change the drive designation to whatever it's listed as under device.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If it doesn't work you can always reinstall the back up.

---

### Post by svelectric on 2007-03-28
I'm sure this is part of my problem.  When I do the command "sudo fdisk -l" it just shows the internal hdd.  It doesn't mention my USB hdd which is plugged in, turned on, and green.  It's just not there...

svelectric@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14417   115804521   83  Linux
/dev/hda2           14418       14593     1413720    5  Extended
/dev/hda5           14418       14593     1413688+  82  Linux swap / Solaris
svelectric@ubuntu:~$

---

### Post by Scarlett on 2007-03-28
Ummmm...... hmmmmm..... I really don't know.

Can you see anything in ~./media?

---

### Post by svelectric on 2007-03-28
It just shows my cdrom drive.

---

### Post by Scarlett on 2007-03-28
I'm sorry, that's about the extent of my knowledge here.  Have you used the search?  Chances are someone else has asked the question and received helpful help.  Good luck!

---

### Post by svelectric on 2007-03-28
I've googled this I've searched on here, I can't find a thing that helps.  Thanks for your help though, much appreciated.

---

### Post by svelectric on 2007-03-28
bump

---

### Post by svelectric on 2007-03-28
bump

---

### Post by Austin_KW on 2007-03-28
Your new disk will be a new device. 
Your first physical disk is /dev/hda and new devices (including your cdrom) will be /dev/hdb /dev/hdc etc

if you do ' ls /dev/hd* /dev/sd*' in a terminal before and after you connect the disk you should see the new device 

USB disks often show up as /dev/sda, /dev/sdb etc
try 'fdisk -l /dev/sda'
or 'gparted /dev/sda'

---

