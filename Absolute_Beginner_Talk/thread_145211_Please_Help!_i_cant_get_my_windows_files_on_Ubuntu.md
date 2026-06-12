---
title: "Please Help! i cant get my windows files on Ubuntu!"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by lanu39 on 2006-03-15
hi to everyone! yes... i decided to mount Ubuntu a few days ago to try it, and i just cant get to correctly mount my windows hard drive on Ubuntu. i cant see my files.

i have 2 hard drives, one 160gb with Windows Xp and the other one 40 gb with Ubuntu installed, and perfectly double boots. the funny thing is that i have 2 partitions on windows and on the ubuntu's desktop i have two shortcuts to this partitions, but when i try to access to them it tells: THE FOLDER CONTENTS COULD NOT BE DISPLAYED: You do not have the permissions necessary to view the contents of "hda2"... i have read a lot of forums and already tried a lot of things but had no results! Please help me with this!

---

### Post by Jedeye on 2006-03-15
check this out [http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows") its what I used when I still had windows. if you have tried modifying your fstab and it gives your trouble, post us the content. Open up the terminal ```
sudo gedit /etc/fstab
``` and just cut and paste the content here.

---

### Post by Weebs on 2006-03-15
I had the same problom and used the link by Jedeye (Auctually this wasy about 30 mins ago :) ). It works great.

---

### Post by lanu39 on 2006-03-15
ok! i already tried that one and it didn't work here is my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0

the hard drive i want to access is the hda2, is the one with my windows files on. 

Thanks a lot for your help!

---

### Post by aysiu on 2006-03-15
Change this ```
/dev/hda2 /media/hda2 ntfs defaults 0 0
``` to this ```
/dev/hda2 /media/hda2 ntfs nls=utf8,umask=0222 0 0
```

---

### Post by Jedeye on 2006-03-15
aysiu is correct. Also make sure the directory "hda2" is in "/media/" and use ```
sudo mount -a
``` after editing fstab to mount the drive

---

### Post by aysiu on 2006-03-15
```
sudo mount -a
``` is the quick way. If you don't mind rebooting, rebooting can also remount everything cleanly.

---

### Post by lanu39 on 2006-03-15
YEEEEEPPEEEERRRRR!!!!! hehehehe it's readyy!!! thanks a lot!! i really appreciate it! hope to learn more about this os! :)  :mrgreen:  :mrgreen:  :mrgreen:  \\:D/

---

### Post by lanu39 on 2006-03-15
just for other people reference, it got solved on rebooting! i couldn't access anyway with the sudo mount -a command. but when i rebooted it works perfectly! thanks again!

---

### Post by lanu39 on 2006-03-15
Now my final question is, i've read so so that it a little risky having the windows partition on Ubuntu, because if for mistake you change something on it you would totally ruin it, is this true?? if it's like this, i would like to set it to read only mode, because i have really important data there, from work and i can't loose it!

---

### Post by Jedeye on 2006-03-15
since it is NTFS it should be read only... you will have to copy it over to exit it.

---

### Post by DCJoeDog on 2006-03-20
[QUOTE=aysiu]Change this ```
/dev/hda2 /media/hda2 ntfs defaults 0 0
``` to this ```
/dev/hda2 /media/hda2 ntfs nls=utf8,umask=0222 0 0
```[/QUOTE]

changing my options to "nls=utf8,umask=0222" is what did the trick for me

then a quick

```
sudo umount /media/hda1
sudo umount /media/hdb1
sudo umount /media/hdd1
sudo mount -a
```

and now I have them all accessible from the default desktop icons

---

