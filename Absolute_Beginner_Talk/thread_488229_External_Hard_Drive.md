---
title: "External Hard Drive"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by jmusso on 2007-06-29
I've got Feisty Fawn installed on my Presario v5000, and I'm trying to format a Western Digital external HD (120gb) into two partitions (probably 90-95% ext3 and then 5-10% NTSF). However, when I select the HD under GParted, there appears to be a little padlock icon next to it. How do I remove this? Thanks.

---

### Post by cwood06 on 2007-06-29
its probbly mounted...
so just unmount it

imo it would be best to do your 90-95% ext3 and the rest in fat32 just so windows can r/w and linux can to

---

### Post by jmusso on 2007-06-29
I've been doing some reading and I've found that if I keep most of in in ext3 I can write all my ubuntu files and what not too it. If I keep a small amount in NTSF, I can load the driver for Windows to recognize ext3 on it, and put small files on it for speedy upload to other windows computers. i'm actually trying to take windows off my laptop completely... hence i need the HD to be compatible with Ubuntu and Windows. Thanks though.

---

### Post by jmusso on 2007-06-29
Okay, I just tried to "unmount" the external HD, and I couldn't. The only option was to "Eject" it when I right-clicked on the icon. And when I tried to do that it wouldn't let me...

---

### Post by trak87 on 2007-06-29
You have a few options:

1) If you just wanted ext3, there is a Windows driver available to read ext3 drives. I can't remember the name of it at the moment.

2) Fat32 is a format natively compatible with both operating systems.

3) If you add the ntfs-3g driver to Linux, you can read/write Windows ntfs partitions.

The first option may be your best choice since your goal is to eventually eliminate Windows.

---

### Post by jmusso on 2007-06-29
Thanks. I was thinking about keeping a small ntsf partition for transporting files to other people's computer that are on my ext3 partition, and just storing the driver your referring to (fs-driver.org i believe) on that ntsf partition for use with people's windows computers. however, as i stated above, I can't seem to partition/format the HD under Gparted... and don't know why.

---

### Post by logos34 on 2007-06-29
> The first option may be your best choice since your goal is to eventually eliminate Windows.

Agree.  Get** fs-driver.**

I think you may need to turn off the removable devices option

gnome-volume-properties

untick the boxes for 'mount removable drives and media'

---

### Post by milambyr on 2007-06-29
You should be able to open a terminal and type "sudo umount /media/devicename" of course replacing /media/devicename with the actual location of the external hdd.

---

