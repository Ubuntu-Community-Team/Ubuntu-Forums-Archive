---
title: "Borked kernel update"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-05-28
I just tried to update the kernel from 2.6.20-15 to  2.6.20-16, and the boot failed, probably cause of automatix,
is this update really needed ??, I just rebooted  to the former kernel and everything is fine now, I know , I had been warned. :o

---

### Post by PetePete on 2007-05-28
it updates various security fixes.
you probably want to work out why it isn't booting with the new kernel, what does your system display when you try and boot? 

what does booting into recovery mode do?

---

### Post by Pobega on 2007-05-28
The only way we can help you is if you tell us what error message you're getting when the kernel tries to boot.

---

### Post by Hobo Joe on 2007-05-28
Re-install your graphics drivers in the new kernel.(You may have to boot into recovery mode)

---

### Post by Drakkor on 2007-05-28
Thanks for the replies, here's the log from /var/log/fsck/checkfs:

Log of fsck -C -R -A -a 
Mon May 28 12:36:37 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sdb3

/dev/sdb3: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Mon May 28 12:36:37 2007
----------------

---

### Post by Drakkor on 2007-05-28
Hmmm........ 

Log of fsck -C -a -t ext3 /dev/hdb1 
Mon May 28 12:36:37 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/hdb1: clean, 171251/2572288 files, 2735784/5120710 blocks

Mon May 28 12:36:37 2007

This seems kind of funny since the failing happened on /dev/sdb3 , which is not the boot partition, and
the log says /dev/hdb1  (sdb1)?  which is the boot partition is clean !  :confused:

---

### Post by turbod33 on 2007-05-29
Hey this happened to me last night. What had happened was the kernel change somehow changed the drive detection order / lettering. I would boot into as far as you can, open a new console (shift f2) and do the following: 

Check your drive names by: 

sudo fdisk -l 

and compare those to the ones in /etc/fstab
more /etc/fstab

---

