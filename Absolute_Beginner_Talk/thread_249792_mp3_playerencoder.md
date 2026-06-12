---
title: "mp3 player/encoder"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by greenie9 on 2006-09-03
im just wondering if there is a way to get an mp3 encoder/player for ubuntu without being connected to the internet.

i have ubuntu installed on a computer that is not connected to the internet, and dont want to have to burn/re-rip all my music to OGG format, when i could just plug in my mp3 player and play it that way...

thanx

---

### Post by kidders on 2006-09-03
What you need is mplayer (which also comes with a thing called mencoder). It's the mother of all media players, better than anything available in either the Linux or Windows worlds :P

Installing it without internet access could be a pain though. My advice is to take a peek in your package manager for mplayer and its dependencies, download them all someplace else, stick them on a USB stick and get them on your machine that way.

Properly configured, mplayer can play pretty much any media format in existence.

---

### Post by kombipom on 2006-09-03
Ubuntu doesn't support mp3 "out of the box" as it is a propriatory codec (not open).  However it is very easy to add mp3 support.  The wiki doesn't seem to be working at the moment but try searching it for Restricted Format and it should come up with some instructions.

---

### Post by whizbaby on 2006-09-03
> **greenie9 said:**
> way to get an mp3 encoder/player for ubuntu without being connected to the internet.


How would you connect to the repositories to install packages then? All I can think of is downloading the packages directly from the repository at a friend's place (or internet cafe or university etc.), burning them on cd and copying them to your computer, then install with dpkg. (If any of these seems non-trivial to you please don't hesitate to ask)

---

### Post by greenie9 on 2006-09-03
i have 2 computers, one connected to the net, one not...

got ubuntu installed on the non-net connected one...

i know a reasonable amount about computers, but not much about linux... so could u please explain it to me...

---

### Post by whizbaby on 2006-09-03
Here are all the ubuntu package repositories:
[http://de.archive.ubuntu.com/ubuntu/pool/](http://de.archive.ubuntu.com/ubuntu/pool/)

Here are all the lists of packages in ubuntu repositories:
[http://de.archive.ubuntu.com/ubuntu/dists/](http://de.archive.ubuntu.com/ubuntu/dists/)

So if you know the name of the program you want download the newest version of it's *.deb with either i386 (normal pc) or amd64 in it's name (depending on your hardware), e.g. mplayer-386_1.0-pre6-0.3ubuntu6_i386.deb for mplayer (in the multiverse repository). But BE AWARE that this way dependencies to other packages are not fulfilled automatically, that means:
after copying the package to your linux home and typing (in a terminal) **sudo dpkg -i *package_name*** (lowest-level (not meaning quality) package manager)

there might/will come error messages whining about this and that not being there - then you have to download that too and copy it to the your home and restart from
 **sudo dpkg package_name** (perhaps a lot of times)
**BUT**
Wouldn't it be a lot easier to connect your ubuntu system to the internet for the time of the installation ?(or connect the two pc'c via network
and route the ubuntu machine into the internet?) Then you could install the way it's meant to be which is a lot easier, faster and safer!
This link is rather usefull for ubuntu/multimedia:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

