---
title: "Need to use make before online"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Sciophobia on 2008-02-05
So my wireless card is only supported by the Madwifi snapshot, or the -mm patch for the kernel.  Problem is, I cant run make without an internet connection since I need other packages to run make.  So is there somewhere I can get all the needed packages in a .deb or something that would let me be able to make without being online?

---

### Post by emarkd on 2008-02-05
You can download the packages you need at [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/).  Try the build-essential package.  It's got all that stuff in one handy place.

---

### Post by spiderbatdad on 2008-02-05
what do you need?  Many of the packages like build-essential are available on the Gutsy CD. Or do you have access to another computer? You could put the stuff on a flash drive.

---

### Post by Dr Small on 2008-02-05
If you have an alternate cd, you can use it as an offline repository :)

---

### Post by Sciophobia on 2008-02-05
> **spiderbatdad said:**
> what do you need?  Many of the packages like build-essential are available on the Gutsy CD. Or do you have access to another computer? You could put the stuff on a flash drive.

I have a Windows partition and a flash drive I can use to get the files from. I was trying out Wubi so I couldn't use a CD as an offline repository.  Is there anything special I have to do in synaptic to use the offline files besides add the CD as a location?

---

### Post by emarkd on 2008-02-05
Nope, but the CD has to be set up as a repository.  If it's just a bunch of downloaded .deb files, you'll install them by just double-clicking them in Nautilus.

---

### Post by Sciophobia on 2008-02-05
> **emarkd said:**
> Nope, but the CD has to be set up as a repository.  If it's just a bunch of downloaded .deb files, you'll install them by just double-clicking them in Nautilus.

OK, thanks.  I'll try out the CD method, and if that doesn't work I'll toss the .debs on a flash drive and report back :-P

EDIT: Posting from Ubuntu 8.04 thanks for the tips!

---

