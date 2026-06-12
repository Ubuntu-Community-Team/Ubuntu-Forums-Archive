---
title: "Live CD on a power pc"
date: 2008-10-02
forum: Apple Hardware Users
---

### Post by tinker123 on 2008-10-02
I made a livecd for a power pc.  A friend at work tried it on an old powerpc laptop.  The livcd started by the screen only displayed horizontal bands of colors.

Any level of powerpc hardware/version above which I know the livecd will work and below which it will not?

---

### Post by paul_mcl on 2008-10-02
How have you configured your kernel? For 64-bit 970s? With AltiVec (G4 and above)? Which exactly is your friend's powerbook (at least: oldworld or newworld)?
Can you publish your distro so I (and maybe others) can test it on my own macs?
Also, take a look at CLFS ([http://cross-lfs.org/files/BOOK/1.1.0/](http://cross-lfs.org/files/BOOK/1.1.0/)) and Finnix livecd distro ([http://www.finnix.org](http://www.finnix.org)).

---

### Post by tinker123 on 2008-10-03
> **paul_mcl said:**
> How have you configured your kernel? For 64-bit 970s? With AltiVec (G4 and above)? Which exactly is your friend's powerbook (at least: oldworld or newworld)?


Neither machine is mine and I don't have access to either.  I made an Ubuntu 8.04 livecd for powerpc chips for a non-tech friend who wants to see what linux is like.  A friend at work brought in his powerpc laptop so I can test it.  I got the download from here:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by sgmorr on 2008-10-04
tinker, I just downloaded the PPC version that you did. In the next few days I'll burn a CD and try to use it live on my G4 iMac. I toyed around with a live CD of Ubuntu (earlier version a couple of years ago and it worked for me at that time). It's kind of tough for a total linux novice (like me) to find out all the ins and outs of all this.

I'm a Mac user on a daily basis and run Tiger 10.4.11 on my G4 iMac.

---

### Post by stmiller on 2008-10-05
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by DGortze380 on 2008-10-05
I recently installed 7.04 on a G3 Pismo ... it was the only release/distro  I could get to load a live cd and install despite a number of reviews and tutorials for other releases/distros. 

First thing to try would be to boot
```

live video=ofonly

```

---

### Post by kaotixx on 2009-10-27
I just tried out Karmic Koala ppc.
But the old mistake is not yet fixed. The system does nor recognize the correct display ! So I heve got a childish resolution of 600 to 800 .Forget it.Its less than on a palm !!!:(

---

