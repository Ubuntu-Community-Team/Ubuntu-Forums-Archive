---
title: "Moving home directory"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-21
I wanted to move my home directory from Ubuntu partition to another partition (hda11). So I did the following:

init 1
mkdir /media/home
mount /dev/hda11 /media/home
cp -rp /home/ /media/home
mv /home /oldhome
edit fstab (to set dev/hda11 /media/home ...)
init 2


Then I restarted. But it complains that it has not found /home/myname after I enter the username and password. 

Is there a certain file in /etc or elsewhere that is still pointing to /home?

---

### Post by pbaehr on 2006-03-21
A simple cp will not work right for this.

Follow this guide:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

That should do it for you.

Good luck.

---

### Post by AtinLango on 2006-03-21
Thanx. I'll try and let u know.

---

### Post by AtinLango on 2006-03-21
Actually it works if it is mounted to /home rather than /media/home


So like this:

```
init 1
mv /home /oldhome
mkdir /home
mount /dev/hda11 /home
cp -rp /oldhome/ /home
edit fstab (to set dev/hda11 /home ...)
init 2
```

Perfect!

---

### Post by pbaehr on 2006-03-21
Oh, yeah, duh. I should've noticed that. Glad you got it working.

---

