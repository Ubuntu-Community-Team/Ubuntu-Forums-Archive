---
title: "question about removing files"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by seek3r on 2007-07-06
Hi, kind of a n00b to Ubuntu, but pretty computer literate otherwise, so here goes:

I have a question about removing files. I was poking around on my system using du just to get an idea of whats on the system, and I found quite a few files of the following type:

/usr/src/linux-headers-2.6.20-16/include/asm-sparc64
/usr/src/linux-headers-2.6.20-15/include/asm-sparc64

/usr/src/linux-headers-2.6.20-16/include/asm-m68knommu
/usr/src/linux-headers-2.6.20-15/include/asm-m68knommu

/usr/src/linux-headers-2.6.20-16/include/asm-sparc
/usr/src/linux-headers-2.6.20-15/include/asm-sparc

They all take up a fairly considerable space on the disk. Since I am not using a sparc, or a 64 bit system, nor a motorola processor, nor do I intend to (the installation in question is on an older PIII laptop) can I remove those files without hurting anything? 

I wouldnt mind having the disk space back, as this is kind of a minmal system (basically I have a 5 gig partition to play with, out of 10 gigs, dual boot with XP.

If I got it right, these are source code files for compiling a new kernel (which I might try someday, but it isnt likely to ever be on anything other than this machine), and I shouldnt need them, yes?

I am using the Feisty Fawn 7.04 basic install, with xfce on top of it, choose sessions at boot.

In retrospect, I probably should have went with Xubuntu, but, hey, I can cope. :) xfce is definitely faster, but a little less stable I think, and gnome is nice, but pretty slow on this machine. I will probably end up getting rid of gnome in the end, but one thing at a time ..........

How about these files? And anybody got some suggestions about anything else that can be removed (I already stripped out all the unneded localization files (just us english for me is all I need, thanx) uninstalled a few applications I didnt like/didnt need and things, ran the apt-get clean and autoclean routines and stuff like that.

Overall I am liking Ubuntu quite nicely, and no real major hardware issues (well, the nVidia restricted driver did kind of whack my X when I tried to use it, but a little searching on the forums found me an answer :D and some minor issues with the xfce4-panel not working right (or at all, sometimes, which I also fixed by searching the forums) -- but on this, I dont find much. How about an "advanced n00b" guide on what can be deleted without killing this precious beast and what should probably be left alone. :D

Thanks for any help.

---

### Post by bodhi.zazen on 2007-07-06
Remove stuff from synaptic or add/remove programs first (ie remove the linux-headers if you are not going to compile).

You can safely delete almost anything in /home, otherwise, as a noob, if you do not know what it is do not delete it.

If you are tight on disk space, you might enjoy a lighter environment like say a server install + light gnome or fluxbox.

Here are some ideas :

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

[http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/](http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/)


You might also like puppy linux.

---

