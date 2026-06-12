---
title: "partition help please ubuntu goes to 40 gigs"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-31
at the moment my disk look like this

isk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2690 21607393+ 83 Linux
/dev/hda2 2691 2809 955867+ 82 Linux swap / Solaris
/dev/hda3 2810 4776 15799927+ 83 Linux
/dev/hda4 4777 4864 706860 5 Extended
/dev/hda5 4777 4864 706828+ 82 Linux swap / Solaris

now on hda1 I have A sementation problem do not worry about the that
I want to increase ubuntu on hda3 to take up the whole disk as I am going
to create a os.img within ubuntu with kqemu

any ideas how to start the partition process with gparted please

lex1;)

---

### Post by Mustard on 2006-03-31
I'm staring at this thinking about it atm. :)

I'm curious about something....

What is the output of the mount command?

```
mount
```

Currently it looks like you have two swap partitions.

---

### Post by lex1 on 2006-03-31
i installed sarge on hda1 but it has a segmentation fault i am going to delete and resize ubuntu hence my question

lex1:(

---

### Post by Mustard on 2006-03-31
[QUOTE=lex1]i installed sarge on hda1 but it has a segmentation fault i am going to delete and resize ubuntu hence my question

lex1:([/QUOTE]

You don't feel inclined to paste the output of 'mount' in this thread (see my first question)?

---

### Post by lex1 on 2006-03-31
here we go

bliss1@xstation:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
bliss1@xstation:~$

---

### Post by lex1 on 2006-03-31
tried 
dd if=/dev/hda3 of=/dev/hda1 ; fdisk e2fsck -f /dev/hda1 resice2fs /dev/hda1 
at the sarge dvd install prompt but alas

dd: /dev/hda3 no such file or direcctory

fdisk invaild option -f

---

### Post by Mustard on 2006-03-31
What's on the /dev/hda4 partition?

The way I see it, and I have to admit to not having a clear picture here,  you would have to delete the /dev/hda4 and /dev/hda5 partitions and that would allow you to increase the size of the /dev/hda3 partion.  I assume /dev/hda2 is going to be the working swap partition for your Ubuntu installation.

---

### Post by lex1 on 2006-03-31
someone suggested deleting partirtion 5
look at
[http://www.debianhelp.org/module-pnForum-viewtopic-topic-11137-start-0.html](http://www.debianhelp.org/module-pnForum-viewtopic-topic-11137-start-0.html)

lex1

---

