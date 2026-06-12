---
title: "dvd-rw not detected"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by LiterallyDude on 2007-07-18
i am using feisty and at some point ubuntu stopped detecting my samsung dvd-rw. it's not listed in the media folder.... i put a disc in and nothing happens... i don't even know where to begin. thanks in advance.

---

### Post by hamburglar6 on 2007-07-19
could you post a copy of your /etc/fstab file?

in the meantime, you can try this:
```
 sudo mkdir /media/cdrom 
```

and then put a disc in the drive and check if any of these work:

```
 sudo mount /dev/cdrom /media/cdrom
sudo mount /dev/cdrom1 /media/cdrom
sudo mount /dev/dvd /media/cdrom
sudo mount /dev/dvdrw /media/cdrom
```

or anything else in your /dev folder which looks like it might work.

---

### Post by LiterallyDude on 2007-07-19
> proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=aa348546-0fce-4e14-afae-8ae4d257b309 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/sdb5 :
UUID=62d8c763-6f61-409f-a2f3-654d8acf8bd3 /home/ed ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# Entry for /dev/sdb6 :
UUID=084da676-5efd-4e33-8546-cd13540edc3b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /home/bak ntfs-3g defaults,locale=en_US.utf8 0 0

thanks!

---

### Post by deadlikeoscar on 2007-07-19
Yep, /dev/scd0 should be /dev/cdrom. Edit your fstab file and change it.

---

### Post by LiterallyDude on 2007-07-21
```
proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=aa348546-0fce-4e14-afae-8ae4d257b309 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/sdb5 :
UUID=62d8c763-6f61-409f-a2f3-654d8acf8bd3 /home/ed ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# Entry for /dev/sdb6 :
UUID=084da676-5efd-4e33-8546-cd13540edc3b none swap sw 0 0
#/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /home/bak ntfs-3g defaults,locale=en_US.utf8 0 0
```

still no dice. what to do now.

thanks.

---

### Post by hamburglar6 on 2007-07-21
when you tried all of those 'sudo mount /dev/xxxx /media/cdrom' before did any of them work?  also throw cdrom0 onto that pile.  you might want to look through your /dev folder and see if there is anything relevant that i missed too.  whichever one works is the one you want to use in your fstab.  also, you might want to change the part where it says "udf,iso9660" to "auto".

---

