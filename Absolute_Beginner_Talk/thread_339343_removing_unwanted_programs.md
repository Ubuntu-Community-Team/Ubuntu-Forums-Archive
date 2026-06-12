---
title: "removing unwanted programs"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by slipperhead on 2007-01-15
i'm running ubuntu 6.06 on a 233mhz/96 ram toshiba laptop (got fed up with xubuntu and i like to experiment) and its surprisingly not too bad.
however, having only a 4 gig harddrive(3.7gb for ubuntu) i would like to get rid of the heavy apps like open office etc.
i managed to remove the gimp but trying to remove openoffice broke synaptic)
so is it possible to remove these apps and can anyone recommend others i could do without?

---

### Post by aysiu on 2007-01-15
I don't see how removing OpenOffice could break Synaptic.

You should be able to remove whatever you want.

Honestly, though, you may have an easier time reinstalling, doing a server install (from the Alternate CD), and then adding only the most basic packages and then any packages you want in addition to that--adding from nothing instead of subtracting from a lot.

After you do **Install a server**, you'll be at the command line. Log in and type ```
sudo aptitude update
sudo aptitude install gdm icewm menu xterm x-window-system-core synaptic firefox
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
``` You can substitute whatever your browser of choice is for Firefox, of course. Once you've logged into IceWM, you can add more stuff using Synaptic.

---

### Post by bodhi.zazen on 2007-01-15
You can also try Fluxbuntu. It is basically a server install + Fluxbox + rox

My Fluxbuntu HD install is 1.4 Gb (I have added a little to the base and updated)

[Main page](http://fluxbuntu.org/)

	[forums](http://community.fluxbuntu.org/)

	[ Download fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

MD5SUM  : 
	> c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso

---

### Post by slipperhead on 2007-01-15
thanks,it would be the logical thing to start from the bottom up so i will try both your suggestions although i'm hesitant to uninstall after it took six hours to get this install done!

i love the transparent toolbars etc, but with the low memory, they arn't doing this laptop any favours!
are those window managers hard to configure, backgrounds etc.?


edited.i'll do some searching and weigh up the pros and cons of icewm versus fluxbox.

---

### Post by aysiu on 2007-01-15
This is my plug for IceWM:
[Anyone else dig IceWM?](http://ubuntuforums.org/showthread.php?t=263710&highlight=dig+icewm)

---

### Post by bodhi.zazen on 2007-01-15
I am also a fan of IceWM and feel it is under rated.

Follow the link in my signature for a nice how-to on the Debian Forums (Thanks Lou)

---

### Post by bodhi.zazen on 2007-01-15
Off topic:

Best way to remove unwanted programs:

```
aptitude purge Vista
```

:lol:

---

### Post by slipperhead on 2007-01-15
> **bodhi.zazen said:**
> Off topic:

Best way to remove unwanted programs:

```
aptitude purge Vista
```

:lol:

lol!

hmmm, wonder if i could get vista on this dinosaur!
i'll try anything once!

checking out the links. both look promising.

---

