---
title: "Mac to PC"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-01-11
Hi there,

Whilst I know a fair amount about Linux and a lot about Windows, I have no idea when it comes to Macs.

My girlfriends P4 motherboard has just died and the only serviceable machine I have available at the moment is a Mac running OS 9.2 (or similar).

She hates Mac with a passion though, would prefer XP but will tolerate me Linux.  So I have a few questions that I hope people can help me with.

1 - How do I find out the current system specs on a Mac?
2 - Is the hardware of the Mac different to that of a regular PC - if not, then will things like RAM, the CD-RW and GFX card from her P4 have a chance of being fitted in there?
3 - How do I go about formatting the HDD so I can install another OS on there?

Thanks in advance guys :)

---

### Post by Pevichaey5 on 2008-01-11
if its not an intel mac, you can't use it

macs are very special, and i hate them way too simple for me

macs don't have a bios or anything

i just know i hate them,

very stable, but i hate them

the graphics card won't fit, if its not an intel mac (seens as its 9.2 no chance)

however, you may be able to reuse the cd rom drive in a normal pc

and you can get linux for powerpc's (the mac your on about) not sure if ubuntu do that though, but [suse](http://software.opensuse.org/) do a powerpc version

---

### Post by Kimm on 2008-01-11
Seems that Ubuntu doesn't do powerpc (The CPU in that machine of yours) anymore. But you should use an older version anyway... to go light on that hardware. The first Xubuntu release perhaps.

Edit:

Fluxbuntu (if available for ppc) might be a better choise.

---

### Post by Squizz on 2008-01-11
So I'm assuming that it isn't Intel (as the Suse site seems to suggest that all Macs made prior to 2006 were non-intel) - is there a way to check?

Also suse ppc says "Sorry, the PPC version is available on DVD and for network installation only." and this Mac surely doesn't have a DVD drive.  Are there any other alternatives?  I'm assuming also that it will boot from a CD automatically as there's no BIOS to play with?

---

### Post by p_quarles on 2008-01-11
To boot from a CD, hold down the c key during the boot process. 

I don't have a lot of experience with Macs, but I know that the shell works similarly to the ones in Linux. So, using the following to get your hardware info is worth a shot:
```
lshw
```

---

### Post by Pevichaey5 on 2008-01-11
macs have never had a bios, which i'm quite surprised myself as i'm doing an A-level in ICT lol

---

### Post by Squizz on 2008-01-11
[http://wiki.fluxbuntu.org/index.php?title=Get#Older_Macintosh_Computers](http://wiki.fluxbuntu.org/index.php?title=Get#Older_Macintosh_Computers) << This is a link to the Fluxubuntu for "older Macs" but it says it's pending build which I guess means that they haven't finished it yet?

Also how do you open the shell?

---

### Post by p_quarles on 2008-01-11
> **Squizz said:**
> [http://wiki.fluxbuntu.org/index.php?title=Get#Older_Macintosh_Computers](http://wiki.fluxbuntu.org/index.php?title=Get#Older_Macintosh_Computers) << This is a link to the Fluxubuntu for "older Macs" but it says it's pending build which I guess means that they haven't finished it yet?

Also how do you open the shell?
Had to look it up. Apparently in Applications >> Utilities:
[https://ucfilespace.uc.edu/wiki/search/108](https://ucfilespace.uc.edu/wiki/search/108)

EDIT: A good bet for PowerPC compatability is Debian. Ubuntu is based on it, and the functionality is very similar:
[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)

---

### Post by Squizz on 2008-01-11
I'll give Debian a try then - if she doesn't like then no worries, as I've never opened up that mac before and now I want to steal the case - never seen such a clean interior!

edit: 22 CDs????  Is that for real?

---

### Post by Niniel on 2008-01-11
System 9.x... that's definitely a PowerPc. However, the last versions did use standard PC hardware, ie. nNvidia graphics cards, HDs, etc... The RAM may be reusable as well. The CD drive should be too, but the older Macs had their "Superdrives" which were slot-in drives, so you may not be able to fit a regular CD drive into the case.

---

### Post by SunnyRabbiera on 2008-01-11
Yeh debian is a best bet for PPC, as most distros have moved away from it

---

