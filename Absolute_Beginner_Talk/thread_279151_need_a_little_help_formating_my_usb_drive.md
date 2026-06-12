---
title: "need a little help formating my usb drive"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-10-17
i just bought a 320 gig seagate IDE drive.
it is currently sleeping in my external icy box usb enclosure.
it is going to be used for storing my media files so the thing is:

1.is gparted ok for formating? or am i better of with command line?

2. what filesystem to put on it? i want one 320 gig parition. since it's going to be used for media stuff what would you recommend? ext3 OK? 

3. how to name my drive so that it isn't sdaX

p.s. it is currently listed as /dev/sda under System>Administration>Disks, so i guess that it isn't mounted (how could it be when it isn't formated? right?)

thnx

EDIT: i just started gparted and it asked to set a disk label. what is a disk label?

---

### Post by grim918 on 2006-10-17
gparted is ok for formatting. It really depends on what you prefer. If you like command line you can use fdisk, if you like GUI's then use gparted. I would recommend that you format the drive into something like fat32, if you are going to be using it for media files. If you ever want to view your media files under windows, then windows will have no problem reading the partition. If you use ext3 then windows won't be able to read it.

as for the drive naming, and disk label I am not sure. You might want to wait until a more knowledgeable person comes along.

---

### Post by zekopeko on 2006-10-17
windows are not a problem. the current problem is that i formated the disk using gparted to ext3 and already there are 4.8 gigs used. what's up with that?

and while am at it how to set the name of the usb disk. currently it is usbdrive and i want to have something like BigStorage or something.
My NTFS disks mount with a name.

---

