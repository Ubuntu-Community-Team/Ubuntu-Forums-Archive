---
title: "downloading package"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by ltho on 2008-03-18
i  only have limited internet access at home ( only after 12 pm) so i want to do the downloading else where, but since all the dependency, it hard to make sure i have download enough. besides, it is tedious. isnt there a better way?? synaptic have a generate download script button, but i dont know what it do.

 one more thing: i try to mount .iso image by using a command, but it there is a cdrom already inside the drive, i cant unmount it later on. something about it had been mount multiple time. any suggestion?

---

### Post by theRightNee on 2008-03-18
well most of the basic ones can be found on the installation CD, so that should be an option...

second is downloading .deb files, [http://www.getdeb.net/](http://www.getdeb.net/)
  should be good...they're just like .exe files

last thing: have you tried unmounting after removing the physical CD?

---

### Post by SOULRiDER on 2008-03-19
You could also ask a friend with Ubuntu to use AptOnCD for you. 
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by ltho on 2008-03-19
so do you know how to use the "generate package download script" function of synaptic??

the command i use to mount .iso image is "mount -o loop -t iso9660 file.iso /media/cdrom"
this is the error i have while trying to unmount "umount: /media/cdrom0 mount disagrees with the fstab"

---

### Post by bruce89 on 2008-03-19
> **theRightNee said:**
> second is downloading .deb files, [http://www.getdeb.net/](http://www.getdeb.net/)
  should be good...they're just like .exe files


They are  all unofficial packages which tend to be messed up.

> **ltho said:**
> synaptic have a generate download script button, but i dont know what it do.


You need another UNIXy computer. You'd need to make the script executable and run it.

---

### Post by zvacet on 2008-03-19
[nonetdebs](http://nonetdebs.homeip.net/)

---

### Post by ltho on 2008-03-20
thank man, nonetdeb is exactly what i need. by the way, how do i change the subject to solved?

---

### Post by kpkeerthi on 2008-03-20
> **ltho said:**
> 
the command i use to mount .iso image is "mount -o loop -t iso9660 file.iso /media/cdrom"
this is the error i have while trying to unmount "umount: /media/cdrom0 mount disagrees with the fstab"

The iso is mounted to **/media/cdrom**. So you unmount it with
```
sudo umount /media/cdrom
```

* Note it is cdrom and not cdrom**0**

I suggest you mount ISOs to an unique folder as /media/cdrom is used for CDs
```

sudo mkdir /media/ISO

```

Mount using
```
mount -o loop -t iso9660 /path/to/file.iso /media/ISO
```

Unmount using
```
sudo umount /media/ISO
```

---

