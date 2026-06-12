---
title: "mounting laptop Hard drive issues"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by afbase on 2006-11-23
I installed an old laptop hard drive into my server with a 44 pin laptop to 40 pin IDE connector.  I am curious as whether that prevents me from writing files onto the hard drive.  If so, then I think i know my problem.

Anyways, If that isn't the case I am have difficulties changing /dev/hdc1 as a read, write drive.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       /home/clinton/hdd1 ext3 suid,dev,exec 0 0
/dev/hdc1       /home/clinton/mysql ext3 suid,dev,exec 0 0


```

I am trying to figure out as to why i get this error message after i type:```
root@Condor:/home/clinton# mount -t ext2 -o rw,remount /dev/hdc1 /home/clinton/mysql


mount: block device /dev/hdc1 is write-protected, mounting read-only


```

---

### Post by afbase on 2006-11-23
here is my ls -l /dev/hdc1
```

root@Condor:/home/clinton# ls -l /dev/hdc1
brw-rw---- 1 root disk 22, 1 2006-11-22 21:14 /dev/hdc1

```

---

### Post by Afishionado on 2006-11-23
Motherboard setting, maybe? Just a wild guess.

William

---

### Post by aosmith on 2006-11-23
I'm thinking its a format problem... the dev/hdc1 is hard to read but i had prblems with an ntfs drive.  could also be a problem with the jumper on the hd

---

### Post by afbase on 2006-11-23
I don't have physical jumpers on my drive.  It was an ntfs drive, but i changed it to ext3 in cfdisk.  

I hope it's not a mobo problem!  I  use a very old supermicro mobo with a dual cpu pIII 8000mhz system.

any other possible ideas?  I know i tried installing ubuntu (hoary, dapper, and edgy)  several times and I had several issues.  On installation, it would allow me to install GRUB but LILO, and the other one was that it would only boot up half way, crash, restart, and never boot again (even if i restarted).  


I'm still looking for other leads on this!!!! thanks

---

### Post by aosmith on 2006-11-25
Actually I'm having the same problem with a hd im using... Are you sure you dont have any physical jumpers? I've never seen an hd without them (check the pinout label on the hd)

---

