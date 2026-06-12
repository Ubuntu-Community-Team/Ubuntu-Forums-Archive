---
title: "do not see my external dvd"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by rccharles on 2006-08-17
I am running ubuntu live version 6.06 (2.6.15-23) on my iMac g3.  I see my external harddrive when I plug it in as USB or Firewire. I do not see my external HP DVD writer 200e neither as USB or Firewire.  When I look in the devices panel.  I see that Ubuntu detects an HP mass storage device, but that is all.  I do not see the DVD in the my computer panel.

How to I access my external HP DVD player?

Robert

---

### Post by wvslkr on 2006-08-17
Have you tried putting a disk in.  Icon normally comes up after loading a disk.  Not mounted till then.

Only thing I can think of at the moment.

GL.

---

### Post by bodhi.zazen on 2006-08-17
If that does not work:

leave the disk in place.

in a terminal:

sudo mkdir /media/dev
sudo mount -t auto /dev/sda /media/dev

You man need to add a number at the end of sda. On some drives try
sda1
sda2
sda3
sda4

I have a zip drive that is always /dev/sda4

Once you can mount the drive you can update /etc/fstab or change the mount point.

---

### Post by The303 on 2007-02-01
I am having the same problem with my external dvd drive HP 840e

I have tried the above advice, but when I do 

sudo mount -t auto /dev/sda /media/dev

I get the message...

sudo mount -t auto /dev/sda2 /media/dev 
mount: you must specify the filesystem type

I have tried many different disks in the drive to mount it, at the moment I have DVD video in there

Can anybody help me please

---

