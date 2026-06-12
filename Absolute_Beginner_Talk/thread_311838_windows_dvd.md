---
title: "windows dvd"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by jasonsexton on 2006-12-03
I am trying to open a DVD archive that I made on an XP box and it fails.  I get a message saying, "the folder contents can not be displayed"  "you do not have the permissions necessary to view the contents of DVD recorder"  Anyone have any suggestions?

---

### Post by taurus on 2006-12-03
Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Then, browse to where the CD-ROM is mounted!!!

---

### Post by jasonsexton on 2006-12-03
well that got me in but I can't see any files.  I tried show hidden files and still nothing visible.  There are files that are visible through XP on the disc.

---

### Post by taurus on 2006-12-03
Assuming your CD is mounted to /media/cdrom0, run this command from a terminal and see what do you get ?

```
sudo ls -la /media/cdrom0
```

---

### Post by jasonsexton on 2006-12-03
this is what I get

drwxr-xr-x 2 root root 4096 2006-09-17 00:10 .
drwxr-xr-x 4 root root 4096 2006-12-03 13:00 ..

---

### Post by taurus on 2006-12-03
Is that where your CD is mounted to?  What's the output of this command?

```
df -h
```

---

### Post by jasonsexton on 2006-12-03
jason@SummerSex:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G   99G   39G  72% /
varrun                440M  120K  439M   1% /var/run
varlock               440M  4.0K  440M   1% /var/lock
udev                  440M  108K  439M   1% /dev
devshm                440M     0  440M   0% /dev/shm
lrm                   440M   22M  419M   5% /lib/modules/2.6.15-27-amd64-generic/volatile
/dev/hdc              4.0G  4.0G     0 100% /media/dvdrecorder
jason@SummerSex:~$

---

### Post by taurus on 2006-12-03
Your DVD is mounted on /media/dvdrecorder, not /media/cdrom0...

```
sudo ls -la /media/dvdrecorder
```

---

### Post by jasonsexton on 2006-12-03
thank you

---

