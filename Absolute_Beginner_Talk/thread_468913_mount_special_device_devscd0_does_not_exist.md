---
title: "mount: special device /dev/scd0 does not exist"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by hyunkell on 2007-06-09
Hello,

I installed Ubuntu 7.04 3 days ago, and until today everything worked fine.
I had a few problems getting my graphic card drivers to work properly, but all of that could be solved by googling.

However, when I tried to insert a dvd today (Ut2004) nothing popped up.
I tried doubleclicking cd-rom 1 in Nautilus and I got:

Unable to mount the selected volume.
mount: special device /dev/scd0 does not exist

Google showed me quite some results, but most about usb dvd drives.
I'm using a laptop, and have an integrated dual layer dvd burner (Oss-dvd is all it says, it's from Toshiba I believe)

This was pretty irritating, so I did a:
sudo cdrecord -scanbus

and got:

scsibus0:
        0,0,0     0) 'ATA     ' 'FUJITSU MHV2120B' '0000' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

here's my fstab:
proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=010f67db-e4df-45fe-9363-0b6e15c53f14 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=ACD460DDD460AAF2 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=113b3920-9d4d-46e4-9ba8-2edb40e76bdf none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user 0 0


This is all pretty weird, it seems that it doesn't recognize my dvd drive at all anymore?

I found another post over google, where someone suggested to install libdvdcss2 from the mediubuntu repository which I did, but unfortunately it was of no help.

I tried a few other cds/dvds, even a dvd that worked 2 days ago, and none of them are recognized.

dvd drive works perfectly fine in xp (dualboot)



I'm wondering, shouldn't my dvd drive be /dev/sd0 rather then /dev/scd0 ?
I'm quite a newbie when it comes to linux, so I'm not really sure what sd or scd stands for, but doing 

ls -l /dev/sg*

I get:
crw-rw---- 1 root root 21, 0 2007-06-09 18:25 /dev/sg0

Should be my dvd drive, or am I misunderstanding something?

Edit:
I tried
hyunkell@hyunkell-laptop:~$ sudo mount -t iso9660 /dev/sg0 /media/cdrom1 (I created cdrom1 ony my own, didn't want to overwrite cdrom0 or anything)

and got
mount: /dev/sg0 is not a block device


Any ideas?
Thanks in advance :)

---

### Post by carloslosgrande on 2007-06-09
You probably upgraded after install? 
Check out this thread;
[http://ubuntuforums.org/showthread.php?t=460092](http://ubuntuforums.org/showthread.php?t=460092)
It may clear things up for you

---

### Post by hyunkell on 2007-06-09
Thanks for your reply,

unfortunately I have no such things in my /dev/ folder, no cdrom/dvd nothing.
I'm also experiencing the same problem in the .15 kernel.

---

### Post by hyunkell on 2007-06-10
*bump*

---

### Post by hyunkell on 2007-06-10
another bump :(

---

### Post by hyunkell on 2007-06-10
Tried a few more things, but nothing was of help.
What could cause Ubuntu to not detect a cd/dvd drive at all anymore anyways?
It really doesn't look like a mounting problem to me :/

---

### Post by cleopete on 2007-06-11
Add me to this problem as well, with pretty much the same info as hyunkell- except mine is a cd burner.  It also shows up in the fstab.

I've only been playing with Ubuntu for a couple of weeks, and tonight is the first time I've attempted to use the cd drive. It may well have been down since the install.  I copied data from my XP system by hooking up  the hard drives and installing ntfs-3g.  I deleted those drives from the fstab when I was finished.

EDIT:
Upon further experimentation I found factory made disks work, but my WinXP-burned discs do not.

---

### Post by pixar on 2007-06-17
I have the same problem!

---

### Post by carloslosgrande on 2007-06-17
Hi, there is a problem with version 16 of the kernel header.
A temporary fix that works is to look in your [COLOR="Blue"]/dev[/COLOR]  folder, note all the [COLOR="Blue"]cd[/COLOR] or [COLOR="Blue"]dvd[/COLOR] devices, eg i have [COLOR="Blue"]cdrom cdrw dvd dvdrw[/COLOR]
then, [COLOR="Red"]after you make a backup of your /etc/fstab file[/COLOR] edit your /etc/fstab file to look something like this;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c174c1a9-0ff0-459f-bd96-d4ef5de3ae8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=27fee279-a1e2-4a08-ad51-ab672d98493b none            swap    sw              0       0
/dev/sdb1 /media/seagate ext3 defaults 0 0
[COLOR="Purple"]/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]
```

the highlighted part being the relevant change. This works for me.

its only a temporary fix until version 17 comes out. Or you can revert to version 15.

I'm a long way from being any sort of expert and this fix wasn't thought up by me (unfortunately). If you're still having difficulties [COLOR="Orange"]you may need to start your own thread[/COLOR] so that someone knowledgeable can see it and help you.

---

