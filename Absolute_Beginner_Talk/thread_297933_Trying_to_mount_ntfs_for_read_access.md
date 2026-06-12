---
title: "Trying to mount ntfs for read access"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by sophenator on 2006-11-11
This is a common question, but I have been unable to solve it with advice through the forum or online guides.  
  I have just installed ubuntu 6.10 with a live cd install and all has apparently gone well, however I don't know how to access my ntfs partition  from ubuntu.  I have tried some commands in terminal, and I may have even created a directory or mounting point. (excuse, please-really  new at this).
  Here are some results in terminal:

 sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7153    57456441    7  HPFS/NTFS
/dev/hda2            7154       14417    58348080   83  Linux
/dev/hda3           14418       14593     1413720    5  Extended
/dev/hda5           14418       14593     1413688+  82  Linux swap / Solaris

 mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

  I am trying to mount windows so I can see the files from ubuntu in the gui.
  As I am so new, I don't want to harm the file system by experimenting further.  I don't think I screwed anything up yet, though.  
  Thanks, any help greatly appreciated.

---

### Post by taurus on 2006-11-11
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by sophenator on 2006-11-11
Thanks, I looked at this and tried some things, but wasn't sure if it was safe to use with 6.10. I didn't want to edit fstab if it would mess things up.

---

### Post by taurus on 2006-11-11
That's why you make a backup copy of your /etc/fstab just in case!  That link works for Dapper and it will also work for Edgy...

---

### Post by crabby on 2006-11-12
i don't mean to be a pain or anything... but all i can find on the forums is howto edit the fstab to mount ntfs partitions. but all i want to do is use the 'mount' command! 

cOuld someone please run through the command to do it and the options required to read/write?

thanks,

crabby

---

### Post by bodhi.zazen on 2006-11-12
> **crabby said:**
> i don't mean to be a pain or anything... but all i can find on the forums is howto edit the fstab to mount ntfs partitions. but all i want to do is use the 'mount' command! 

cOuld someone please run through the command to do it and the options required to read/write?

thanks,

crabby

[fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

