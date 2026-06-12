---
title: "Installing onto a partition"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Ringo Mountbatten on 2007-04-11
I have two hard drives in Windows XP, c: and d:, XP is loaded into the c drive, my d drive is for various music/video files, and I used partition magic to split the d drive into 2, with 50gb (g: drive) to install ubuntu on til I see if I prefer that.

The problem is when I run through the ubuntu install process, I can't specify that I want ubuntu to install to the g drive, or as ubuntu calls it hd5. Instead all I can see is that ubuntu wants to resize my 2nd physical drive on its own terms which I'm very wary of because I dont want to risk losing any of the media I have saved on there. So I just cancelled the installation.

Am I worrying too much and ubuntu will avoid the data already on the 2nd drive? Thanks for any help

---

### Post by thefoolisme on 2007-04-11
You could choose manual partition and go that way, but then you would have to know a little bit about partitioning in Linux.  Then you could choose exactly where you want it to go, and how big the partitions should be.  See [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) for a good explanation.

---

### Post by annda on 2007-04-11
you can safely choose manual partitioning. BUT you need TWO partitions for linux: the so-called root (mounted as "/") and swap (mounted as "swap"). so you will probably end up deleting hda5 and creating two new partitions in that space. it's really easy, not more difficult than partition magic.

good luck!

---

