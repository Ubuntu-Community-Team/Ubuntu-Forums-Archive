---
title: "Mounting a Linux partition"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-07
Okay - I know this is going to sound like a dumb question - but how do I mount a new Linux partition??

Here's the scenario.... I've installed both Ubuntu and Fedora Core 6 on the same hard drive. Ultimately, I'll use a shared partition that they can both see - but the moment, I don't have a big enough hard drive. Therefore I need to set up Ubnuntu so that it can see the Fedora partition (which is apparently /dev/hda2). I went into **fstab** and added the following line:-
[B]
/dev/hda2       /media/hda2     ext2    defaults        0       2[/B]

I expected to see the Fedora partition mounted as a volume, next time I re-booted but it doesn't work... :( If I go into Places->Computer, the Fedora partition isn't even shown. Do I need to place an entry somewhere else, as well as fstab?

---

### Post by indytim on 2006-12-07
Do you have a hda folder in /media?

IndyTim

---

### Post by John E on 2006-12-07
I have hda3 and hda4 (Windows 2000 and Windows XP respectively) but no hda or hda2.

---

### Post by taurus on 2006-12-07
Paste the output of this command here???

Applications -> Accessories -> Terminal
```
ls -la /media
```

---

### Post by John E on 2006-12-07
Here's what I got:-

```
drwxr-xr-x  8 root root     4096 2006-11-23 20:02 .
drwxr-xr-x 21 root root     4096 2006-12-07 12:17 ..
lrwxrwxrwx  1 root root        6 2006-11-22 09:53 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2006-11-22 09:53 cdrom0
drwxr-xr-x  2 root root     4096 2006-11-23 20:02 floppy
drwxr-xr-x  2 root root     4096 2006-11-22 09:52 hda3
drwxr-xr-x  2 root root     4096 2006-11-22 09:52 hda4
```

and here's the contents of fstab:-

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda2       /media/hda2     ext2    defaults        0       2
/dev/hda3       none            vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       none            vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by bodhi.zazen on 2006-12-07
```
sudo mkdir /media/hda2 && sudo mount -a
```

---

### Post by John E on 2006-12-07
Yes, that seems to have done it. Thank you...!

---

