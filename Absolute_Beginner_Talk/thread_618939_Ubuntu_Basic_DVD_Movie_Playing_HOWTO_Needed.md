---
title: "Ubuntu Basic DVD Movie Playing HOWTO Needed"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Budly on 2007-11-20
I have been trying to figure out how to play some movies that I have on DVD with Ubuntu. I am having very little success. I have tried to go through lots of the various web pages about plugins for Totem and codecs and such and I can not make much sense out of all these pages. 

Can someone help me setup playing ordinary movies (or is my idea of what constitutes an ordinary movie DVD  the problem?) like   Ïn the Heat of the Night  or   The Hunt for Red October?

I am willing to spend some time on this to understand all the various media formats but I dont have a place to start.

---

### Post by mouseboyx on 2007-11-20
Open the synaptic package manager:
System > Administration > Synaptic Package Manager


Click search and type gstreamer

shift+click to select all packages that start with the word gstreamer and install them.

You should now be able to play any media format in The movie player/totem/xine

---

### Post by Paul820 on 2007-11-20
For encrypted DVD's you need libdvdcss2 to play them.

---

### Post by mikewhatever on 2007-11-21
The place to start --> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by kevin11951 on 2007-11-21
ok... i had your problem too... and i have a solution that will work, its one line in the termanal, and it makes it so you can use all encrypted dvds! check if you have 

libdvdread3

installed, if you do, your nearly done, if you dont no problem (its in the repos)... now then after you install it or whatever, run the code that comes with it: 

sudo /usr/share/doc/libdvdread3/install-css.sh

Done! play dvds to your harts content (dont know why that way isnt more publicized?)

---

