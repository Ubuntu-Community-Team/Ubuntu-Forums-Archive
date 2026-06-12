---
title: "Unable to verify any packages"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-03
I'm having problems getting anything installed because for some reason most of them show unable to verify.

---

### Post by pieisgood4589 on 2008-02-03
> **Liet_Kynes said:**
> I'm having problems getting anything installed because for some reason most of them show unable to verify.

Most of what? PLEASE people, just state all the facts and computer specs, or I'll kill you! Jesus Christ! :mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by pieisgood4589 on 2008-02-03
> **pieisgood4589 said:**
> Most of what? PLEASE people, just state all the facts and computer specs, or I'll kill you! Jesus Christ! :mad::mad::mad::mad::mad::mad::mad:

Sorry 'bout that, just got a bit angry...:(

---

### Post by ichbinesderelch on 2008-02-03
did you have internet access during installation? if not there might be the problem that he disabled all sources, so check out administration --> package sources(cant remember exact name) and enable packagesources! or just edit /etc/apt/sources.list by hand if you prefere text mode ;)

---

### Post by jan quark on 2008-02-03
pieisgood4589 keep your temper...

:)

and yes you should check your soruces

either by terminal as stated above or go to the sources window in the menu and check all available sources except the last ones, except source code and CD

---

### Post by Liet_Kynes on 2008-02-03
I had internet connection on install.  But now e.g i tried to apt-get install kppp and I got a msg saying about 4 of the dependent libraries could not be verified. What could have happened. I've tried apt-get update and still the same results

---

### Post by ichbinesderelch on 2008-02-03
did you check your sources?

---

### Post by SunnyRabbiera on 2008-02-03
most of these kinds of errors mean nothing, and are normally harmless.
This usually comes from adding more repositories but its normally not a big issue.

---

### Post by Liet_Kynes on 2008-02-03
WARNING: The following packages cannot be authenticated!
  liba52-0.7.4 libgsm1 libavcodec0d libdc1394-13 libavformat0d libdvbpsi4
  libdvdnav4 libdvdread3 libid3tag0 libiso9660-4 libmad0 libmodplug0c2
  libmpcdec3 libmpeg2-4 libpostproc0d libsdl-image1.2 libtar libvcdinfo0
  libvlc0 libwxbase2.6-0 libwxgtk2.6-0 libxosd2 vlc-nox vlc


So should I ignore them or how do I go about fixing the repositories?

---

### Post by SunnyRabbiera on 2008-02-03
eh ignore it, this message is just a "just in case" kind of thing...
most of those packages I am familiar with and I would say its safe enough.


By the way: Arrakis... Dune... Desert planet :D

---

### Post by Liet_Kynes on 2008-02-04
> **SunnyRabbiera said:**
> eh ignore it, this message is just a "just in case" kind of thing...
most of those packages I am familiar with and I would say its safe enough.


By the way: Arrakis... Dune... Desert planet :D


Thanks I was getting worried there.


"Walk without rhythm and you won't attract the worm" :)

---

