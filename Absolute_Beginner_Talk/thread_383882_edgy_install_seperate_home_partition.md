---
title: "edgy install /seperate home partition"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-03-13
i just installed edgy with a seperate root and home  partition but i dont know if i can see my home partition,

this is my fstab 

                ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=78b8510c-1b57-4c12-849c-14f1a7a6bcc4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=423d214d-f5f6-4e49-9e85-bef426f8e925 /home           ext3    defaults        0       2
# /dev/hdb5
UUID=ae9ba5e1-185f-4146-8831-1c3c4072c13c none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /fat_files vfat iocharset=utf8,umask=000 0 0

```
hdb3 shows up as home  it is just the wrong size 
any ideas

---

### Post by gangrelsurf on 2007-03-13
What size is it, what size is it supposed to be and what did you do to find the size?

---

### Post by STREETURCHINE on 2007-03-13
i manually partitioned it so it 15 gig root partition and a 59 gig home partition,
when i click on home it only shows as 11 gig free space

and this is  the output of df -h

```
rex@rex-rex:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              15G  2.8G   12G  20% /
varrun               1014M   84K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   21M  994M   2% /lib/modules/2.6.17-11-386/volatile
/dev/hdb3              58G  359M   55G   1% /home
/dev/hda1             187G  111G   76G  60% /fat_files
rex@rex-rex:~$
```

---

### Post by STREETURCHINE on 2007-03-14
bump

so i figure i have not got it mounted so i would like to know how to mount it so i dont get the wrong permissions

---

### Post by gangrelsurf on 2007-03-14
I more or less have to admit ignorance on this one.

Your fstab looks straight. Your df output plainly shows plenty of space, but not in gnome (I assume you mean right clicking on it and properties). I'm afraid I don't have any solutions for you. I hope some one else on here does.  But the next thing I would check for clues is:

```
du -hs /home
```

and just see if that gives the same value as df -h

Beyond that, I might run fsck on it.  If you try that, read the man page first. You'll have to log into the rescue mode (from grub in boot up) and make sure that the disk is unmounted. See if it gives you any errors, take it from there.

wish i could be more help

---

### Post by STREETURCHINE on 2007-03-14
thanks it is ok i completely fried the system so i reinstalled and upgraded to edgy,but now my grub keeps crawling away,
so i am trying to fix that at the moment

---

