---
title: "fstab &amp; device.map"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-03-02
Hi all! Having checked /etc/fstab I have no entries. The same applies to device.map.
Why is that?
regards

---

### Post by taurus on 2007-03-02
If /etc/fstab is empty, then you won't be able to boot since it doesn't know where your / partition is.

---

### Post by Sbarton on 2007-03-02
That's what I thought but I boot each time, no problems. See attachment.

---

### Post by bodhi.zazen on 2007-03-02
You need to open the files with root powers ...

sudo nano /etc/fstab

OR

gksudo gedit /etc/fstab

---

### Post by overdrank on 2007-03-02
> **Sbarton said:**
> That's what I thought but I boot each time, no problems. See attachment.

I get the same and I am on a raid. I believe that is why I get that.

---

### Post by steve101101 on 2007-03-02
the fstab should look something like this...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=05e22853-8435-46f9-9f78-d603805f0a06 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0082ba95-85c8-4ec2-825e-41d911119304 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by overdrank on 2007-03-02
> **bodhi.zazen said:**
> You need to open the files with root powers ...

sudo nano /etc/fstab

OR

gksudo gedit /etc/fstab

Thanks (sudo nano /etc/fstab)  worked   Learn something new everday!:)

---

### Post by steve101101 on 2007-03-02
I am unsure how you can even boot because nothing is mounted.

---

### Post by Sbarton on 2007-03-02
The 'sudo nano' works for me, but why not with sudo? Hi Paul capps, I don't have raid so that would not be my reason.
regards

---

### Post by taurus on 2007-03-02
Or just

```
cat /etc/fstab
```

---

### Post by Sbarton on 2007-03-02
Thanks for all input. 'sudo nano', 'cat', and 'gksudo'worked fine. I still don't know why 'sudo gedit'
did not work though!
regards

---

### Post by bodhi.zazen on 2007-03-02
You should use gksudo with graphical apps :

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Sbarton on 2007-03-02
bodhi.zazen, see attachment for each time I use 'gksudo' Why the warning?
regards

---

### Post by bodhi.zazen on 2007-03-02
From my recollection this is a bug and has been reported. Does the application (gedit) open ?

[http://ubuntuforums.org/showthread.php?t=366671](http://ubuntuforums.org/showthread.php?t=366671)

[https://launchpad.net/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/ubuntu/+source/gksu/+bug/23917)

---

### Post by Sbarton on 2007-03-02
It opens following the warning!
regards

---

### Post by bodhi.zazen on 2007-03-02
> **Sbarton said:**
> It opens following the warning!
regards

It is a known bug, see my previous post, low priority ...

---

### Post by Sbarton on 2007-03-02
Thanks for info and links.
regards

---

