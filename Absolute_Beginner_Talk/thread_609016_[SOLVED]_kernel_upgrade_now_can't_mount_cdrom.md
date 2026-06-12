---
title: "[SOLVED] kernel upgrade now can't mount cdrom"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by haggus on 2007-11-10
I upgraded my kernel last night using the master kernel thread everything compiled w/o errors I can boot my new kernel but now I can't mount any cdrom trhey are listed in /etc/fstab and I can see them in root media I must have done something wrong can someone point me in the right direction

/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/hda ntfs-3g defaults,locale=en_CA.UTF-8 0 0

I'm running a gateway Gt5012 Pentium dual core 1.8 Ghz 1Gb ram two SATA WD 250 Gb

Looking at these lines is the noauto possibly a problem?

---

### Post by Happy_Man on 2007-11-10
Hmmm.... is HAL running all right?

```
sudo /etc/init.d/hal start
```

---

### Post by haggus on 2007-11-10
Gives me 
@ubuntu:~$ sudo /etc/init.d/hal start
Password:
sudo: /etc/init.d/hal: command not found
@ubuntu:~$ sudo /etc/init.d/hal-start
sudo: /etc/init.d/hal-start: command not found
@ubuntu:~$ sudo /etc/init.d/hal.start
sudo: /etc/init.d/hal.start: command not found
@ubuntu:~$ sudo /etc/init.d/hal.start

---

### Post by haggus on 2007-12-01
> **haggus said:**
> I upgraded my kernel last night using the master kernel thread everything compiled w/o errors I can boot my new kernel but now I can't mount any cdrom trhey are listed in /etc/fstab and I can see them in root media I must have done something wrong can someone point me in the right direction

/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/hda ntfs-3g defaults,locale=en_CA.UTF-8 0 0

I'm running a gateway Gt5012 Pentium dual core 1.8 Ghz 1Gb ram two SATA WD 250 Gb

Looking at these lines is the noauto possibly a problem?

I ran this

sudo modprobe ide_generic

everything working fine now

---

