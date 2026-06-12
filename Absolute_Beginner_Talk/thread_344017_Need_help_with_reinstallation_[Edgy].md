---
title: "Need help with reinstallation [Edgy]"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by optimarcus_prime on 2007-01-22
Well, I've given up hope for restoring my system [you can see the thread of my problem [here]("http://ubuntuforums.org/showthread.php?t=343048")].  So, I'm going to reinstall Edgy and give it another go.

Before I can do that, I need to recover some data off of the apparently corrupted hard drive, such as:
-Folders on my desktop and in my home folder
-Thunderbird Emails
-Firefox bookmarks
-If possible, I'd like to make a list of all the programs I had installed

I've been struggling to do this because I can't even manage to view my old file system when running on a LiveCD.  I have an external hard drive that I can copy the items that I want onto, although I don't know how to remount it.  So, any and all help would be most appreciated.

[If you think you can help me with the [original problem]("http://ubuntuforums.org/showthread.php?t=343048"), that would be even more appreciated!]

---

### Post by kidders on 2007-01-22
Hi there,

I scanned over your other post. It's ... well ... strange! I wonder what would happen if you unplugged your CD drive, and tried to boot again.

> I've been struggling to do this because I can't even manage to view my old file system when running on a LiveCD.This is quite worrying ... what kinds of error messages do you get when you try?

---

### Post by optimarcus_prime on 2007-01-22
> **kidders said:**
> This is quite worrying ... what kinds of error messages do you get when you try?

I don't get any errors.  The problem isn't an error, it's the fact that I don't know *how* to do it.  :) 

I'll try the CD drive removal bit.  I'll post what happens.

---

### Post by optimarcus_prime on 2007-01-23
**UPDATE:** OK, so what I've tried so far is that I've installed another partition of Ubuntu onto the computer so that I can use it to access the old partition.  The problem is now that for some reason when I try to mount the old partition, the system tells me that it is unmountable.  I get the same error whether I am attempting from the actual temp. installation or from the LiveCD:
```
marcus@domo:~$ sudo mount /dev/hda1 /mnt
Password:
mount: special device /dev/hda1 does not exist

```

I don't understand this because I know that the old partition is on hda1, since on the boot-up screen where I choose which partition to use, the old on has "(On /dev/hda1)" next to it.  Any thoughts?

---

### Post by kerry_s on 2007-01-23
Try> sudo mount /media/hda1
then go to /media and look in the /hda1 folder

and post your /etc/fstab so we can see what your drives are.

---

### Post by optimarcus_prime on 2007-01-23
I tried what you suggested, kerry_s, and got the same error message.  This is the file you suggested:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=befc9c20-6e6b-4d5b-abe6-969b29d2fcd8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=b6b4feb2-84ab-4d5d-b122-533f0c9729af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I am fairly new to ubuntu, so i can't make heads nor tails of that, so any help is appreciated.
My friend has suggested the use of Knoppix, is that what you would suggest?

---

### Post by optimarcus_prime on 2007-01-23
Ahha!  Problem solved.
```
sudo mount /dev/sda1 /mnt
```
Did the trick.
Now all that's left is hunting down all the files I need.  Thanks for the help.

---

