---
title: "[SOLVED] Can't find &amp;quot;/home&amp;quot; after resizing the home partition"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-22
hi ya

i did the dumb thing of resizing my home which is on a seperate partition

i resized the home by taking 30GB off it and making it into a windows fat32 so the children can have windows for games (i havn't put windows on it yet)

i can get up to the login screen then after putting in the login name and password it can't find my home anymore coz i resized it, so thats as far as it goes, after that message it goes back to the login screen again.

well i checked with knoppix and all the files are still intact in home and useable

is there anyway using a live cd that i can tell it where home is?

(screenshots are posted below in one of the posts)

---

### Post by forestpixie on 2007-09-22
I think that the UUID would have changed although I'm not completely sure, I have a vague recollection of a similar problem, if you're fstab is referenced it in that way - it wouldn't be able to find it. Fstab should show which drive has the /home mount point.

> # /dev/hda2
UUID=dabb09c2-964c-466d-a039-cde4c30d23f8 [COLOR="Red"]/home [/COLOR]          ext3    defaults        0       2

Try ```
blkid
``` in a terminal, then check your fstab, in /etc/fstab - if the UUID doesn't match, backup fstab and then edit ti to match.

```
sudo cp /etc/fstab /etc/fstab.bak.2209
```

```
gksudo gedit /etc/fstab
```

---

### Post by MozartlovesUbun2 on 2007-09-22
========

sorry that didn't help

========

---

### Post by alienexplorers on 2007-09-22
Please list here the output of the > blkid command and also list your fstab file here. > cat /etc/fstab

---

### Post by MozartlovesUbun2 on 2007-09-22
I can post a few screenshots here, is that ok?

or is there a seperate place to upload pictures?

Hope this helps to solve the issue, thx

First 2 pics with the black screen are from the boot

2nd two colour pics are from "safe mode" login, thats as far as it goes

---

### Post by vanadium on 2007-09-22
Resizing a partition does not alter the UUID and this is confirmed on your screenshots. This shows that your sda2 is effectively found. However, the resizing went wrong as the file system clearly has badly been damaged. The only option I see is to do as the log tells: check the disk manually from within recovery mode. If indeed you can access the drive using knoppix, then you could rescue or saveguard data first if needed.

---

### Post by MozartlovesUbun2 on 2007-09-22
here is some help i got from IRC XChat

wastrel says:

<wastrel> ubuntu_: mount /dev/sda2 /home

<wastrel> ubuntu_: ok first make a backup copy  cp /etc/fstab  ~/fstab.bak

<wastrel> ubuntu_: then  nano /etc/fstab   and change the line for your /home   (find the line with "/home" on it) and delete the part that says UUID=<long number> , replace it with "/dev/sda2" (if sda2 is where your homedirs are, and it mounts ok when you try it manually)

=====================

[B]ok i could login now and home folder was there

as soon as i restarted i have the same problem again

help please!!![/B]

---

### Post by vanadium on 2007-09-22
You will also be able to log in by changing the ending 2 to 0 (to disable checking). However, this will not solve the issue that your volume is corrupt.

---

### Post by MozartlovesUbun2 on 2007-09-22
ok i just wanna be able to login in now to save all my data and

then i will do a fresh reinstall

how can i do that please

---

### Post by MozartlovesUbun2 on 2007-09-22
> **vanadium said:**
> You will also be able to log in by changing the ending 2 to 0 (to disable checking). However, this will not solve the issue that your volume is corrupt.

sorry where exactly do i do that?

will i be able to access home then?
---

---

### Post by forestpixie on 2007-09-23
vanadium means change the numbers on the end of your fstab entry, but as he says the volume will still have problems. Although if you can get to the data through knoppix perhaps do it that way.

```
gksudo gedit /etc/fstab
```

If you're happy to reinstall I'd do so in this order

install windows and make sure you do the updates and let it configure itself after the restart
 
then install ubuntu

---

### Post by alienexplorers on 2007-09-23
You may have to go into your fstab file andchange the end 2 to a 0 for /dev/sda2

---

### Post by alienexplorers on 2007-09-23
Some info about mounting partitions:
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by MozartlovesUbun2 on 2007-09-23
> **alienexplorers said:**
> Some info about mounting partitions [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm) :

**Thx dude thats one hell of a nice link there, recommend it to anyone**

I havn't scrapped my system yet, I'll still try and rescue it, just reading through the link u provided me, it's a lotta stuff there, some of it i don't understand, let's see how it goes, i'll post back here

thx
[B]
(this link here too)[/B]  1:  [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) - 2: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

