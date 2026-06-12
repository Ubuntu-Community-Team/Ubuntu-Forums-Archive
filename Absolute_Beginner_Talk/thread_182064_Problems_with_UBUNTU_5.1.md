---
title: "Problems with UBUNTU 5.1"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Lucidio on 2006-05-25
Good day to all!

I installed recently Ubuntu 5.1 in my PC...unfortunally i have a few problems with it, so until the date i´m a dual boot user because i can´t get all the benefits i expected from my distro.

Between the things i cant do are:
Connect to Internet.....................Winmodem, Dial-up Connection
Mount my USB FLASH MEMORY..................Error recognizing the device
Mount my Floppy Unit...................Innate problem for Breezy.

I decide to deal with my problems one at a time, so the most important thing to do is mount my USB Flash Memory because i need it to transport information between my pcs (work and home). Also i´ll be able to google around in windows while i sercah information to resolve my problems with UBUNTU.

The procedure i was using to mount my usb (with no succes, and after hours searching in internet) is:

$ tail -f /var/log/messages..............to discover the device node of my USB, sometimes tis command throws me **sda** and sometimes throws me **sdb**.

Next i use:
$ sudo fdisk -l.............to find out what devices are attached, the partition node and the the format. Throws me:
 Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *           1        1021      126573    6  FAT16

Next i create the folder to mount the device:
mkdir /media/usb

Then i edit the fstab:
$ sudo cp /etc/fstab /etc/fstab_backup
$ sudo gedit /etc/fstab

Adding the next line:
/dev/sda1   /media/usb   vfat   iocharset=utf8,umask=0000   0   0

For last, i save the file and try the commands:
$ sudo mount /media/usb.............or
$ sudo mount -a..............both throws me the error:
The device /dev/sda1/ doesn´t exit or something like that.

please i need assistance, resolving this i´ll be able to resolve easily my others issues with UBUNTU, because i denied to renounce on it, and i dont want to be a dual boot user anymore,,,!

Please HELP! :-k

---

### Post by Sef on 2006-05-25
> Adding the next line:
/dev/sda1 /media/usb vfat iocharset=utf8,umask=0000 0 0

Here's a different way I found of doing that line.

> /dev/sda1     /mnt/usb     vfat    noauto, users, rw, exec, umask=0033

[http://www.linuxforums.org/forum/linux-newbie/11249-usb-flash-disk.html]("http://www.linuxforums.org/forum/linux-newbie/11249-usb-flash-disk.html")

---

### Post by mishranurag on 2006-05-25
If you are installing now, I would recommend you to install Dapper (6.06) rather than Breezy (5.10) :). It should take care of more than half of the problems as such.
Anurag

---

### Post by Lucidio on 2006-05-29
Sorry!

that line didn`t work for me...the message "special device dev/sda1 doesnt exist" still showing up!
when i enter in that directory i can see only sda but no sda1...i think that is the problem...how can i resolve this?

---

### Post by steve.horsley on 2006-05-29
I have come across some USB sticks that don't have a partition table - you mount the entire drive rather than a partition on it. So rather than mount /dev/sda1 which is the first partition on the drive, try mounting /dev/sda instead. 

However, this contradicts your printout from fdisk that clearly says you have a FAT16  (type 6) partition on /dev/sda1. I really don't see how fdisk can tell you about /dev/sda1 if it's not there in /dev. Still, it can't hurt to try.

---

