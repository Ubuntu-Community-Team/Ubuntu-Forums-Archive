---
title: "chowning mounted Windows drives"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-22
Hello,
I have a Windows drive that is automatically mounted (it appears on my Desktop when I start-up).  I wanted to write some files to that drive, but don;t have permission.  I wanted to chown that drive, but can't find its real location...can anyone tell me how to chown it??  Thanks!

---

### Post by evilghost on 2007-01-22
You can't chown a non-Linux filesystem, if I had to guess the partition is NTFS and is mounted read-only.  You need the experimental NTFS-3g module:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by steve.horsley on 2007-01-22
Is it an NTFS drive? If so, you can't write to it at all - you will need to install ntfs-3g first. Writing to NTFS is still regarded as experimental and possibly dangerous.

If it's FAT, you should be able to, but you need to have it mounted with the right parameters. 

Post the output of these two commands and we should be able to figure out what to do:
[B]mount
sudo fdisk -l[/B]

---

### Post by stoer on 2007-01-22
> **bcs said:**
> Hello,
I have a Windows drive that is automatically mounted (it appears on my Desktop when I start-up).  I wanted to write some files to that drive, but don;t have permission.  I wanted to chown that drive, but can't find its real location...can anyone tell me how to chown it??  Thanks!

You can't write to an ntfs drive / partition (without specialist software), you can read from it. You could however, create a fat32 partition that both linux and windows can read from and write to.

---

### Post by ComplexNumber on 2007-01-22
i have all the ntfs stuff, and i can't write to it neither. then again, that doesn't bother me at all because i don't need to write to it.
it obviously requires something else in addition to installing those packages (and, possibly, slightly editing the fstab file).

---

### Post by bcs on 2007-01-22
Thanks everyone for the info.The mounted drive is ntfs, and its not worth installing new anything to write to it.  Just out curiousity, check the output of ```
mount
sudo fdisk -l
``` 
and the ntfs drive is flagged as the boot drive...I thought I was booting from linux partition (that is the default drive that I boot into)..?
```

brian@lin2:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/sda7 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda3 on /media/sda3 type vfat (rw,utf8,umask=007,gid=46)
brian@lin2:~$ sudo fdisk -l
Password:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        6379    51199155    7  HPFS/NTFS
/dev/sda3            9140        9545     3261195   db  CP/M / CTOS / ...
/dev/sda4            6380        9139    22169700    5  Extended
/dev/sda5            6380        7399     8193118+  83  Linux
/dev/sda6            7400        7654     2048256   82  Linux swap / Solaris
/dev/sda7            7655        9139    11928231   83  Linux

Partition table entries are not in disk order
brian@lin2:~$

```

---

### Post by Hanzerik on 2007-01-22
Well, unless you have the Dell XP OS reinstall disk, I would not mess with /dev/sda1 or /dev/sda3.

I would say get a thumb drive that is formated fat32 and use that to transfer files between the two OS's.

Now when I bought my Dell laptop a few months ago, I made sure to get the OS reinstall disk for $10 more. I knew for a fact I was going to blow the laptop away as soon as I got it and dual boot it.

---

### Post by steve.horsley on 2007-01-22
sda3 looks odd to me - I don't recognise the ID tag. 

Grub doesn't pay much attention to the boot flag, although it can set the flag if needed to keep the chosen boot OS happy.

---

### Post by bcs on 2007-01-22
Cool; sounds good.  Thanks all.

---

### Post by Buck2348 on 2007-01-22
> **steve.horsley said:**
> sda3 looks odd to me - I don't recognise the ID tag. 

sda looks like the (5 gig or so) partition Dell used to put on a system for a complete restoration of the machine to its state at delivery, including preinstalled software.

---

### Post by bcs on 2007-01-22
Yeah, you're right.  sda3 is the windows recovery partition that dell shipped with it.

---

