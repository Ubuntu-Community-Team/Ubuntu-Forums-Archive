---
title: "help mounting remote volume"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-10-11
hello,

whenever I try to access my jungle disk remote volume, i get the following result:
```
steve@darwin:~$ mount /home/steve/DAV
/usr/lib/mount.davfs-2.6: No mountpoint specified

```

an icon called "DAV" shows up under "Computer," but is inaccessible.

here's my fstab:
```
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
http://localhost:2667/   /home/steve/DAV   davfs   user,noauto   0   0


```

what am i doing wrong?

i've tried accessing it using the "connect to server" dialog, but this gives me phantom files that are not accessible.

thanks,

-steve

---

### Post by stevieb on 2006-10-12
please help!

---

### Post by Ocxic on 2006-10-12
Try:

//localhost:2667/   /home/steve/DAV   davfs   user,noauto   0   0

or

localhost:2667/   /home/steve/DAV   davfs   user,noauto   0   0

---

### Post by stevieb on 2006-10-12
no dice, but thanks anyway.  still get "no mountpoint specified."  i tried turning off jungledisk first, and got the following:

steve@darwin:~$ sudo mount /home/steve/DAV
/usr/lib/mount.davfs-2.6: No mountpoint specified
[2]+  Done                    ./jungledisk  (wd: ~/jungledisk)
(wd now: ~)


-steve

---

### Post by stevieb on 2006-10-14
is this a simple syntax issue in the fstab or something deeper?

---

### Post by Ocxic on 2006-10-14
try removing the "/" at the end of the "localhost:2667/"

and the command require a device to mount and a mount point so is should be:

sudo mount "/what_your_mounting/" "/your_mount_point/" (without the quotes.)

---

### Post by stevieb on 2006-10-14
thanks; here's the result:

steve@darwin:~$ sudo mount /http://localhost:2667/ /home/steve/DAV
mount: can't get address for /http

---

### Post by Ocxic on 2006-10-14
try just:

sudo mount localhost:2667 /home/steve/DAV
or
sudo mount 127.0.0.1:2667 /home/steve/DAV

I just want to make sure you know that localhost/127.0.0.1 is your own computer, scince you say your trying to connect toa remot volume.

---

### Post by stevieb on 2006-10-14
yes, i understand that.

here's what i got:
steve@darwin:~$ sudo mount localhost:2667 /home/steve/DAV
mount to NFS server 'localhost' failed: server is down.
steve@darwin:~$ sudo mount 127.0.0.1:2667 /home/steve/DAV
mount to NFS server '127.0.0.1' failed: server is down.

---

### Post by Ocxic on 2006-10-14
what is this jungle disk thing???
why do you have to connect to it like this, if your running it from your computer???


edit: I'll troll this post for the next half hour or so, my replies will be quick.

---

