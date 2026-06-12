---
title: "What is &quot;Floppy1&quot;"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-11-01
Hi all,
I run a new Edgy installation. Under "Computer" the file browser shows a drive icon with the name "Floppy 1", and the icon "Floppy Drive" for the physical existent floppy drive. When I try to access "Floppy 1" I get the error message: > Unable to mount the selected floppy drive. 
mount: /dev/ is not a block device
[COLOR="Blue"]What is Floppy 1? Do I need it? Can I eliminate it? How?[/COLOR]

---

### Post by Roobert on 2006-11-01
Post the output from:

```
ls -al /media
```

---

### Post by BLTicklemonster on 2006-11-01
It has a swish looking arrow on it, doesn't it? Like it's a link to something? do you have one for your cdrom, also?

---

### Post by Roobert on 2006-11-01
Yeah, that was what I was thinking - maybe it's a symbolic link to the floppy drive.

---

### Post by Tamil on 2006-11-01
> **Roobert said:**
> Post the output from:

```
ls -al /media
``````
tamil@08:59:44 ~ $ ls -al /media
total 32
drwxr-xr-x  8 root root 4096 2006-10-31 19:47 .
drwxr-xr-x 21 root root 4096 2006-10-28 11:49 ..
lrwxrwxrwx  1 root root    6 2006-10-27 16:16 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-10-27 16:16 cdrom0
lrwxrwxrwx  1 root root    7 2006-10-27 16:16 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2006-10-27 16:16 floppy0
drwxr-xr-x  2 root root 4096 2006-10-31 19:47 floppy-1
drwxr-xr-x  2 root root 4096 2006-10-27 16:16 sda1
drwxr-xr-x  2 root root 4096 2006-10-27 16:16 sda2
drwxr-xr-x  2 root root 4096 2006-10-27 16:16 sda3
```

---

### Post by BLTicklemonster on 2006-11-01
ticklemonster@ticklemonster:~$ ls -al /media
total 65
drwxr-xr-x 12 root root   336 2006-11-01 20:56 .
drwxr-xr-x 22 root root   656 2006-10-29 10:42 ..
lrwxrwxrwx  1 root root     6 2006-10-28 17:55 cdrom -> cdrom0
drwxr-xr-x  2 root root    48 2006-10-28 17:55 cdrom0
drwxr-xr-x  2 root root    48 2006-10-28 17:55 cdrom1
lrwxrwxrwx  1 root root     7 2006-10-28 17:55 floppy -> floppy0
drwxr-xr-x  2 root root    48 2006-10-28 17:55 floppy0
drwxrwxrwx 16 root root 16384 1969-12-31 18:00 hda1
drwxr-xr-x 22 root root  4096 2006-10-17 20:24 hda3
drwxrwxrwx 15 root root 16384 1969-12-31 18:00 hda5
drwxr-xr-x  2 root root    48 2006-11-01 20:55 hda6
dr-x------  1 root root 28672 2006-09-22 18:05 hdb1
drwxr-xr-x 22 root root   656 2006-10-29 10:42 hdd1
drwxr-xr-x  2 root root    48 2006-11-01 20:56 hdd2


OOOH WHEEEE I got a bunch of crap.

---

