---
title: "how do you mount a drive?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-24
If I have an external hard drive / mp3 player, how do I mount it?  It shows up in the "device manager" thing, but there's nothing there for mounting.  I tried downloading and running mountpy, but it didn't see it.  I found a program for the mp3 player, and I installed it (the dependencies were already installed), but I have to mount the thing before I can use the program on it.

---

### Post by philippe_carlo on 2006-07-24
[http://ubuntuguide.org/wiki/Dapper#Windows]("http://ubuntuguide.org/wiki/Dapper#Windows")

---

### Post by macogw on 2006-07-24
that "assume /dev/hda1" thing is the problem...i used /dev/hdb1 like is mentioned [here](http://ubuntuforums.org/showthread.php?t=222099), but when i type mount /media/data (like those directions say) "mount: special device /dev/hdb1 does not exist" appears.  So, how do I find the ACTUAL location of it because some made-up variable location doesn't help.

---

### Post by OU812 on 2006-07-25
Finding device names:

For hard drives

sudo /sbin/fdisk -l

For usb drives

sudo dfisk -l

To find out which ones are already mounted

df

Mounting and unmounting:

To mount a usb device

sudo mount -w -o noatime /dev/sda1 /memstick

To unmount usb device

sudo umount /memstick

john

---

### Post by 3rdalbum on 2006-07-25
If the USB device isn't mounting automatically, you first need to create a directory to use as a mount point:

sudo mkdir /media/usbdisk

Then actually mount the drive:

sudo mount /dev/sdf1 /media/usbdisk

When you want to unmount it, do:

sudo umount /media/usbdisk

---

