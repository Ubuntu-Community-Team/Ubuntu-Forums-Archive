---
title: "usb mounting problem"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-03-04
I tried to use amarok to play stuff directly from my ipod by setting it to look for files in /media/ipod and it made a horrible noise and locked up.  I turned off my computer and rebooted it and now ubuntu doesn't mount any usb devices...any idea how to fix this?

---

### Post by Pragmatist on 2006-03-04
type: ```
tail -f /var/log/messages
``` in a terminal.  Then plug in the ipod and watch the text that appears in the terminal.  Look for a device file like /dev/sdxy  where x is a letter and y is a number (like /dev/sda1 or /dev/sdc5)

---

### Post by ryan on 2006-03-06
I am having a similar problem.

Trying to mount a 60GB USB 2.0 drive here is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 	/home/ryan	ext3	defaults,user_xattr 1  2
/dev/sda1       /media/USB60G vfat user,umask=000 0 0

Here is the error message I get:

ryan@ryan:~$ sudo mount -a

mount: special device /dev/sda1 does not exist

Disks manager identifies the USB drive as /dev/sda1

Any ideas tks

---

### Post by Sutekh on 2006-03-06
[QUOTE=ryan]

Here is the error message I get:

ryan@ryan:~$ sudo mount -a

mount: special device /dev/sda1 does not exist

[/QUOTE]
Can I ask a dumb question?  ;) 

I get that exact error with my MP3 player, if I try a **sudo mount -a**, when the device is not plugged in.  Could you check the connection?  

Another thought, it may also be a problem that people have with removable media, and that is the device identifier (/dev/sd#) can change depending on what removable devices are plugged in.  For example your USB drive might be sda, but if something else (another USB) is plugged in before it, the USB drive might become sdb.

Try ```
sudo fdisk -l
```When you are sure the USB is plugged in.  This will list all the partitions on all the devices connected.  Make sure that the device entry (/dev/sd#) for the USB drive matches the device entry(/dev/sd#) in the /etc/fstab

---

### Post by Pragmatist on 2006-03-06
> sudo fdisk -l ... This will list all the partitions on all the devices connected. 
It was a nice idea, but actually thats not what fdisk -l does.  To quote the man page for fdisk:
> -l     List the partition tables for the specified devices and then exit.  If no devices are given, those mentioned in /proc/partitions (if that exists) are used.

I just plugged in my palm pilot and got an entry when I checked /var/log/messages, but there is no change in my /proc/partitions file, nor does anything other than hard drive partitions and something called (dm) show up.

My recommendation is the same.  Try to find the device file currently attributed to the device you want to mount.  To do this, try ```
tail -f /var/log/messages
``` and look for a line containing /dev/sdxy where x is a letter and y is a number.

Also, you can try: ```
lshal
``` to list the hal devices that are recognized by the system.

---

### Post by ryan on 2006-03-06
Ok tks very much I will check try doing this. I appreciate your help.

---

### Post by Sutekh on 2006-03-06
[QUOTE=Pragmatist]It was a nice idea, but actually thats not what fdisk -l does.  To quote the man page for fdisk:
> Quote:
-l List the partition tables for the specified devices and then exit. If no devices are given, those mentioned in /proc/partitions (if that exists) are used.
[/QUOTE]
I didn't realise this at all, I noticed that fdisk -l showed my USB when it was connected and not when its unconnected.  Didn't realise it had to 'exist' before that could happen.

Thanks for the info

---

### Post by ryan on 2006-03-08
Tks for all of your input it seems that the drive now is picked up by the system when I plug it in I am not sure what happened or what I did differently, this is the way it should work.

The system monitor identifies it as:
/dev/sda1 /media/New Volume vfat 

I did comment out this line in fstab

#/dev/sda1 /media/USB60G vfat user,umask=000 0 0

---

