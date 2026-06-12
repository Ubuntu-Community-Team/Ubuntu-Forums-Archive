---
title: "Reinstall ubuntu without cd?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-05-15
Hi I want to format and reinstall my ubuntu.
Is it possible to do so without any ubuntu cd?

James

---

### Post by LaRoza on 2007-05-15
I don't think so. Where did you get Ubuntu originally?

---

### Post by the_axiom on 2007-05-15
A livecd that is broken nowdays...

---

### Post by juantovarm on 2007-05-15
Download it again and install from there

---

### Post by the_axiom on 2007-05-15
When I download it comes as an ISO file, how am I supposed to run that one without burning it? Is there any app that let me mount ISO?

---

### Post by jhenager on 2007-05-15
> **the_axiom said:**
> When I download it comes as an ISO file, how am I supposed to run that one without burning it? Is there any app that let me mount ISO?

[http://ubuntuforums.org/showpost.php?p=2587749&postcount=5](http://ubuntuforums.org/showpost.php?p=2587749&postcount=5)

---

### Post by the_axiom on 2007-05-15
> **jhenager said:**
> [http://ubuntuforums.org/showpost.php?p=2587749&postcount=5](http://ubuntuforums.org/showpost.php?p=2587749&postcount=5)

Couldn't get it to work.
Lets say I have a file called ubuntu.iso on my desktop, how should I run it?

---

### Post by brim4brim on 2007-05-15
> **the_axiom said:**
> Couldn't get it to work.
Lets say I have a file called ubuntu.iso on my desktop, how should I run it?

ISO is the format for disc images (all the files stored on a CD in one file).  You can open it with archive manager but to run it as a CD without burning to CD, you'd need to mount the image on a Virtual drive.

---

### Post by the_axiom on 2007-05-15
Ok and how do I mount the image on a Virtual drive?

---

### Post by trak87 on 2007-05-15
> **the_axiom said:**
> Lets say I have a file called ubuntu.iso on my desktop, how should I run it?

To mount an iso, try this:

```
sudo mkdir /media/somemountpoint
sudo mount ubuntu.iso -r -t iso9660 -o loop /media/somemountpoint
ls -l /media/somemountpoint

```

---

### Post by the_axiom on 2007-05-15
> **trak87 said:**
> To mount an iso, try this:

```
sudo mkdir /media/somemountpoint
sudo mount ubuntu.iso -r -t iso9660 -o loop /media/somemountpoint
ls -l /media/somemountpoint

```

got it to work, needed to cd to dekstop xD

---

### Post by the_axiom on 2007-05-15
But how do I run the installation?

-r-xr-xr-x  1 root root     42 2006-05-28 16:36 autorun.inf
dr-xr-xr-x 10 root root   6144 2007-04-15 15:51 bin
dr-xr-xr-x  2 root root   2048 2007-04-15 15:52 casper
dr-xr-xr-x  6 root root   2048 2007-04-15 15:51 disctree
dr-xr-xr-x  3 root root   2048 2007-04-15 15:51 dists
dr-xr-xr-x  2 root root   2048 2007-04-15 15:52 install
dr-xr-xr-x  2 root root  14336 2007-04-15 15:52 isolinux
-r--r--r--  1 root root  38394 2007-04-15 15:52 md5sum.txt
dr-xr-xr-x  2 root root   2048 2007-04-15 15:51 pics
dr-xr-xr-x  4 root root   2048 2007-04-15 15:51 pool
dr-xr-xr-x  2 root root   2048 2007-04-15 15:51 preseed
dr-xr-xr-x  7 root root   2048 2007-04-15 15:51 programs
-r--r--r--  1 root root    221 2007-04-15 15:51 README.diskdefines
-r-xr-xr-x  1 root root 255358 2007-03-25 18:28 start.bmp
-r-xr-xr-x  1 root root  38912 2003-11-17 18:09 start.exe
-r-xr-xr-x  1 root root     95 2005-06-29 10:23 start.ini
lr-xr-xr-x  1 root root      1 2007-04-15 15:51 ubuntu -> .
-r-xr-xr-x  1 root root 193110 2006-05-28 16:36 ubuntu.ico

---

### Post by trak87 on 2007-05-15
I've never tried to run an installation from an iso mount so I can't say. I would search Google. It seems I've been reading about remote installations for years (like via FTP) but I've never done it.

---

### Post by the_axiom on 2007-05-15
Anyone else got any idea? Im in desperate need of reinstalling ubuntu.

---

### Post by trak87 on 2007-05-15
The topic was discussed here:

[http://ubuntuforums.org/showthread.php?t=98451](http://ubuntuforums.org/showthread.php?t=98451)

---

### Post by oilchangeguy on 2007-05-15
just follow this guide on how to create a cd from an iso file:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

i'm sure what you are asking can be done. however alot of time is being wasted, and if you'll follow the guide, in about an hour you'll be back up and running ubuntu again. you're making something that's very simple into something needlessly hard.

---

### Post by the_axiom on 2007-05-15
Excuse me if I didn't make it clear enough, but I do **not** have any empty-cd at the moment.

---

### Post by oilchangeguy on 2007-05-15
> **the_axiom said:**
> Excuse me if I didn't make it clear enough, but I do **not** have any empty-cd at the moment.

go buy some. a ten pack of cd/r's is not that expensive. and if you'll burn a cd then you'll have it if you need to reinstall, and won't have to go thru this again.

---

### Post by the_axiom on 2007-05-15
Yes you're right. But I thought maby if it was possible I could have Ubuntu running today.
Is there anyway to reset ubuntu to the settings I had from the very start?

---

### Post by the_axiom on 2007-05-15
bump

---

### Post by engla on 2007-05-15
It should be possible to use a netinstall cd or otherwise a cd *image*: Use gparted to create a new, small, blank ext3 partition. Copy the cd bit-by-bit to that partition and set up grub to boot from it and take the install from there.

I'm pretty sure I've heard about this method, but you need further instructions. I don't know where to find it, you and me can both google.

edit: perhaps searching for how to install without cd drive (that's essentially what you want to do) can help..

---

