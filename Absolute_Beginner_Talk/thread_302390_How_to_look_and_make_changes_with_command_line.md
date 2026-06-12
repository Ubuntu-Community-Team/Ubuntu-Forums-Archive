---
title: "How to look and make changes with command line"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-11-18
Hi

I currently have 2 hard drives connected to my laptop.
1 hd is internal.
1 usb hd  is external.

The external is usb and has (2) ext3 partitions.

one of the usb partitions shows up as "usbdisk" and the other partition shows up as "usbdisk-1" on my desktop. I use first (usbdisk) for another spare Edgy OS and the other (usbdisk-1) as a place for backup files.

I can see, make changes, and move files to both partitions with the GUI interface.

My question is how to access these partitions with the command line interface instead of the GUI.  I know most want to use the GUI to access everything but I am different. I like options.

Thanks

NOTE: in other words now the command line interface only has access to internal hd, how do I change to other external hd. (example in DOS to change to another hd you enter "D:" to access the D drive.

---

### Post by bernied on 2006-11-18
You need to learn how to use /etc/fstab and the 'mount' and 'umount' commands. Read about them with the 'man' command in a terminal. 
So,
man mount
man umount
man fstab

If you don't know what a terminal is, read this:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

You will also need to use a text editor as root user. I prefer nano. So,
sudo nano /etc/fstab

Devices are all in the /dev/ directory, but don't try to edit them there. Hard drives are usually /dev/hdxy or /dev/sdxy where x is a, b, c etc and y is the partition number 1, 2, 3 etc

And you may have to make a mountpoint, which is just a directory where a device can be mounted. If you want these devices to show up on the desktop, I think you should use a directory in /media/ So,
sudo mkdir /media/testmount
mount -t ext3 /dev/sda1 /media/testmount
just *might* mount that external usb disk, but maybe not. To see what devices are where, try:
sudo fdisk -l

And,
man fdisk
to find out what you did.

*** Be very careful ***
Read about commands before you use them.

Enjoy

---

### Post by bernied on 2006-11-18
And you can use the 'mount' command without any parameters to see what is already mounted and where.

And also try,
df -h
to see what filesystems you have mounted and how much space is on them.

There is more, keep exploring

---

### Post by CatKiller on 2006-11-18
> **kent41 said:**
> NOTE: in other words now the command line interface only has access to internal hd, how do I change to other external hd. (example in DOS to change to another hd you enter "D:" to access the D drive.

You're wrong in your assertion that you're only looking at an internal hard drive. **Everything** on your computer is a file in a unified filesystem tree. You might want to read [this page]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for an overview.

You already have those partitions mounted (otherwise, you wouldn't be able to access them at all) - meaning that the filesystems on those partitions have been inserted into your filesystem tree at a particular point. This point is almost certainly a sub-directory of **/media**, since you've got icons on the desktop. They might be mounted at /media/usbdisk and media/usbdisk-1 from what you've said, but you'll have to look.

In which case, you'd want ```
cd /media/usbdisk
``` or ```
cd /media/usbdisk-1
``` to access them.

Honestly - "drive letters" :roll: ;)

---

### Post by kent41 on 2006-11-18
I figured it out with the trial and error method.  :D 

It was as simple as 

```
cd /media/usbdisk-1
```

This took me to the  usbdisk-1 external hd.

Thanks for you help

Note: CatKiller   Thanks if you look at the times we came to the same conclusion at the same time. You have it right.
                  It was so simple It just took me awhile to figure it out. In the future I will try not to use drive letters  LOL Thanks again.

---

