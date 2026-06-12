---
title: "Viewing content from Mac HD on Linux"
date: 2008-09-21
forum: Apple Hardware Users
---

### Post by (pr) on 2008-09-21
Hi all,

I've just installed Ubuntu (8.04) on a first gen MBP. I used [this link]("https://help.ubuntu.com/community/MacBookPro#Installing Ubuntu on a MacBook Pro"). And I've made a mistake somewhere with fstab. In the 'Places'-menu I can "see" my Macintosh HD ("HD"). I can open it. Go to my own user dir ("pr"), can see the dir "Music", but can't open the map. I've tried the command: ```
 sudo chmod 755 /media/Macintosh
```, but it doesn't work.

I feel I've made a mistake with [this section]("https://help.ubuntu.com/community/MacBookPro#Access%20OS%20X,%20Windows%20Partition%20&%20Network%20Shares").

This is how gedit fstab looks like right now (I'm rather sure that my Macintosh HD is on /etc/sda2 and is called "HD")

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9033f8ae-6b64-447a-8002-f2347bb0e43f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=2babd361-f62f-4396-8134-c265b3f12d8f none            swap    sw              0       0
/dev/sda2 /media/Macintosh hfsplus rw,exec,auto,users 0 0

```

Any help would be lovely. Thx.
P.

---

### Post by tiresia on 2008-09-21
Have you made the directory for your Macintosh partition?
Please post ```
ls /media
```
If you don't see /media/Macintosh, you should run
```
sudo mkdir /media/Macintosh
mount -a
```

---

### Post by cyberdork33 on 2008-09-21
> **(pr) said:**
> Hi all,

I've just installed Ubuntu (8.04) on a first gen MBP. I used [this link]("https://help.ubuntu.com/community/MacBookPro#Installing%20Ubuntu%20on%20a%20MacBook%20Pro"). And I've made a mistake somewhere with fstab. In the 'Places'-menu I can "see" my Macintosh HD ("HD"). I can open it. Go to my own user dir ("pr"), can see the dir "Music", but can't open the map. I've tried the command: ```
 sudo chmod 755 /media/Macintosh
```, but it doesn't work.
You need to be VERY VERY careful when changing permissions like this on your OSX files. If you changed permissions on all files in that directory, OS X would likely no longer boot up. 

I think you probably followed those steps OK. The issue is that the owner of the files onyour OS X partition and your Ubuntu user are not the same. Therefore Ubuntu sees those files as belonging to another user, and you are denied access. You should boot into OS X, and change the permissions on items in your Home directory to be read all.

---

