---
title: "Ubuntu 7.10 on Powerbook G4"
date: 2008-02-18
forum: Apple PPC Users
---

### Post by Cows on 2008-02-18
Hey everyone, I have a Powerbook G4 667 Mhz with 256 MB Ram and I installed Ubuntu 7.10 doing the following :

* Putting in CD
* Holding down C
* Typing :
```
live-nosplash-powerpc video=ofonly break=top

modprobe ide-core
exit

```
* Boots up to the Desktop
* Opened up Partition Editor to find that there are 3 partitions.
```
/dev/hda1 - Unknown Partition ( Maybe Mac Label ? )
/dev/hda2 - Free Space
/dev/hda3 - HFS+ ( Mac Partition )

```

It doesn't let me create a ext3 partition as /dev/hda2 so I went into the installer and selected guided install and use the whole hard drive. It created ext3 as /dev/hda3 and swap as /dev/hda4, Ubuntu installed. I turn on the computer and this is what happens :

* Stage 1 - pressed l
* Yaboot - Linux
* It continues then a grey screen appears with some words then the screen turns black and It just stays there with a solid " _ ". I was wondering if this is where I'm suppose to open up terminal and add in the "ide-core" but when I press ctrl - option - f1 it doesn't do anything, like if it kernel panic. Also when I was installing, I could see my screen refreshing itself, How do I fix this? I know it has to do with refresh rate.

---

### Post by stream303 on 2008-02-18
Looks pretty normal, although it probably reflects your install cd setup.  When guided partitioning uses an entire disk, the first partition is the Apple partition, the second partition is the boot partition, partition 3 is your ext3 Linux partition, and 4 is your swap.

You can do it manually if you like without too many problems, although very early G3 iMac users will want to keep the whole works to something like 7.5 gB max.

Doing it manually is easy
[http://ubuntuforums.org/showthread.php?t=322872](http://ubuntuforums.org/showthread.php?t=322872)

Looks like you had to use kernel parameters to get the install cd to work.  Now that it is installed, have you tried some of the same combinations at the HD yaboot boot: prompt

Linux video=ofonly
or
Linux video=ofonly break=top

along with your modprobe ide-core etc..

---

### Post by Cows on 2008-02-18
No I haven't tried that. I tried Linux-nosplash-powerpc and it didn't work. I'm reinstalling Ubuntu again though cause I thought i made a mistake. Also I could see my screen continuously refreshing itself. Does this have to do anything with refresh rate? Should I change xorg.conf's Vertical Sync etc..?

---

### Post by stream303 on 2008-02-18
For the least amount of hassle, I'd probaby use the "alternate" text-based installers of either Gutsy or Feisty.  Sounds like you've got the powerpc-faq and known issues handy:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

A trip to editing /etc/X11/xorg.conf sounds reasonable.  I'd have to search the threads here a bit for G4 powerbook tips and what kind of video card you have.  Let's see if we can get you to boot, and at least to a virtual terminal

---

### Post by Cows on 2008-02-18
Alright I tried the Linux video=ofonly break=top and modprobe ide-core , exit and it worked. I'm on the desktop with the normal errors like broken sound and my refresh rate is all messed up. I'm trying to fix it atm.

It says that my video card is :

ATI Radeon Mobility M6 LY

EDIT :

For some reason when I drop into a shell like tty1 , I don't see any text. It's just a black screen.

I'm disabling DRI to see if that fixes it.

---

### Post by stream303 on 2008-02-18
Or you could chicken-out like I would, and install Feisty and see what that xorg.conf looks like and try it on Gutsy. :)

---

### Post by Cows on 2008-02-18
Lol not yet. I almost fixed the refresh rate problem. I had to do the gtf command. Now all I need to find out is the VertRefresh and HorizSync.

---

### Post by stream303 on 2008-02-18
Are you using the ATI or the RADEON driver?  Does changing them make any difference?

I'd be cautious about not having your display at the wrong settings for too long a stretch.

From our friends at Gentoo, lot's to chew on here!
[http://tstotts.net/linux/gentoopb.html](http://tstotts.net/linux/gentoopb.html)

That append line he talks about looks interesting.

---

### Post by Cows on 2008-02-19
I got it. It only starts getting blurry when I reset the gdm so I just restart.

2 more problems so far :

Why when I press ctrl + option + f1 It drops me to a blank screen instead of a terminal (tty1) ?

Every time I restart I have to type exit at the initramfs busybox... I added ide-core and updated but it still drops me to initramfs.. Can't I just boot directly into Ubuntu?

BTW:  I have a "Onyx" Powerbook G4 667 mhz.

---

### Post by stream303 on 2008-02-19
I'm running out of ideas especially since I don't own an ati based Mac. :)

As for the virtual terminals, I wonder if you've tried any of the following boot parameters:
(I'm just using 1024x768 as an example, don't know what your native resolution is)


Linux video=radeon
or
Linux video=radeonfb
or
Linux video=radeon:1024x768
or
Linux video=radeonfb:1024x768
or
Linux video=radeonfb:1024x768-24@60

Maybe some other radeon users can jump in.  Have you tried some of the ati/radeon tweaks for X11 in the big ppc faq?

[https://wiki.ubuntu.com/PowerPCFAQ#head-faa36f4765cc2dec98f5d029183807b8ccd9a954](https://wiki.ubuntu.com/PowerPCFAQ#head-faa36f4765cc2dec98f5d029183807b8ccd9a954)

---

### Post by Cows on 2008-02-19
Alright I fixed it. What I did was I went into my /etc/yaboot.conf and removed the "video=ofonly" and that fixed the virtual terminal problem.

EDIT: Alright I fixed it. The problem was that I had "break=top" in my "append" section of /etc/yaboot.conf. It looks like break=top makes you go into a busybox. Also if you have "splash" in the "append" section then remove it if you are having problems with "video=ofonly" once you remove the splash you wont need "video=ofonly".

Thanks for the help :).

---

### Post by stream303 on 2008-02-19
Right on - glad that worked!

Could you post your yaboot.conf and xorg.conf files here?

---

### Post by Cows on 2008-02-19
Lol I deleted my 7.10 after I fixed it.. I'm on 7.04. I did post my xorg.conf though in one of my recent posts.

---

