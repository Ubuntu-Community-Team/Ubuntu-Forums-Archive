---
title: "Install File Copy Error"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by gijoecam on 2008-03-15
Finally got the system to recognize my hard drive.  Now, when I go to install Ubuntu on that drive, it appears to partition fine, but when it attempts to write the files to the hard drive, I get this message:

>  [Error 5] Input/Output error
This particular error is often due to a faulty cd/dvd disc drive or a faulty hard disk.  It may help to clean the CD/DVD, to burn the cd/dvd at a lower speed, to clean the cd/dvd drive lens, to check whether the hard disk is old or in need of replacement or to move the system to a cooler environment.

The drive is clean, the hard disk is new, and the system is running with an open case, so short of putting it outside, I can't make it any cooler.  The disc checksum program showed that the burned disc was identical to what it should be...  I'm lost, and I've about lost it in dealing with this program...  I'm absolutely clueless now...

Anyone got any ideas on where to go from here to get it to install?

Also, I suspect this will be the answer to the next question:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb4f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13182   105884383+  83  Linux
/dev/sda2           13183       25978   102783870   83  Linux
/dev/sda3           39188       77825   310359735    5  Extended
/dev/sda4           25979       39187   106101292+  83  Linux
/dev/sda5           77448       77825     3036253+  82  Linux swap / Solaris
/dev/sda6           77070       77447     3036222   82  Linux swap / Solaris
/dev/sda7   *       39188       76691   301250817   83  Linux
/dev/sda8           76692       77069     3036253+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda7 on /target type ext3 (rw)
ubuntu@ubuntu:~$ 


I've tried re-running the install multiple time, as you can tell.  It's just cluttering up the drive with partitions, but nothing useful...

Lost again....

-Joe

---

### Post by jan quark on 2008-03-15
hmm I would use the gparted live cd to clean up the duplicated and not needed partitions and install once again. clean and tidy

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

but let's wait for someone other to answer

---

### Post by gijoecam on 2008-03-16
Thanks!

Should I be able to boot to that app directly from the CD it's on?  If so, I can't seem to make it happen...  Once Ubuntu is up and running, the gparted app comes up in the program, but not directly from the CD...  Maybe I'm missing something?  I'm still an extreme newbie here, so be gentle...

-Joe

---

