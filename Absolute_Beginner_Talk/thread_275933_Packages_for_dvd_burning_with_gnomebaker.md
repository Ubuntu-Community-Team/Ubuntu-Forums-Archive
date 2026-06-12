---
title: "Packages for dvd burning with gnomebaker"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by endorfin on 2006-10-12
What packages do I need in order to be able to write dvds with gnomebaker?

---

### Post by michux on 2006-10-12
> **endorfin said:**
> What packages do I need in order to be able to write dvds with gnomebaker?

There is a neat tool for checking the dependencies and recommended software for certain packages:

```
$ sudo apt-cache show gnomebaker
[...]
Recommends: dvd+rw-tools, gstreamer0.8-mad, gstreamer0.8-flac, gstreamer0.8-vorbis
```


You probably need dvd+rw-tools which has the support for growfs filesystem.

---

### Post by endorfin on 2006-10-12
I already got dvd+rw-tools. I also installed the *-flac and *-vorbis packages now. But I still get the same problem: the dvd seems to be burnt but when I put it in the drive it mounts and it says it's a blank disk even though I have already burned it..

---

### Post by endorfin on 2006-10-12
That also seems to be the actual problem: that even though the disk is written, it appears to be empty. Why does this keep on happening? ](*,)

---

### Post by puppy on 2006-10-12
The current version of GnomeBaker in Ubuntu Edgy has a known bug that won't even allow me to burn discs (i.e. it keeps trying to tell me to load discs into my DVD-ROM drive). There are other bugs too so I don't think it's very stable right now

Can I suggest that you might want to consider, for the moment, installing K3B (the KDE CD/DVD burning app) instead of using GnomeBaker. It's very fully featured, and looks great :) 

Sorry that I can't help with your problem, but sometimes I find that instead of ](*,) with apps that won't play ball, I'm better off installing one of the alternatives so that I can be productive again

---

### Post by endorfin on 2006-10-12
Thanks for the reply, but I keep getting the same result with k3b as well. Omg! I gotta find a way to figure this out. My hd is getting full. 

Why do the disks appear to be empty even though they are written??

---

