---
title: "Cannot download mplayer"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by petteri on 2005-12-01
Hello, I searched and read though some threads about how to install Mplayer but I cannot get it to work.  I've enabled the "multiverse" according to this:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

but I'm still getting this error:

petteri@ubuntu:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386

So what is my next step? Thanks!

Peter
Miami, FL USA

BTW: Other than getting Mplayer installed and a printer issue (that for another day!) I'm loving Ubuntu!

---

### Post by frodon on 2005-12-01
It shouldn't be difficult, it's in synpactic. However you need to enable the good repositories.
You can edit manually your source.list file which contain the definition of the repositories.

All is explained in this link : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by Pablo_Escobar on 2005-12-01
If the problem is still there post Your /etc/apt/sources.list here :)

---

### Post by petteri on 2005-12-01
Oh oh! 

I am in the middle of downloading these packages, but I just noticed that I'm not running "breezy" I have 5.04 installed! What now?

Should I at this point since I have nothing of vaule on my Linux partition just d/l a CD image of Breezy and install that?  Can I just re-format my linux partition from the Breey CD? Ugh, I wish I woudn;t have missed that!

---

### Post by frodon on 2005-12-01
lol, an update works just fine in most of the case and will keep all your settings, the instructions are here : [https://wiki.ubuntu.com/BreezyUpgradeNotes?](https://wiki.ubuntu.com/BreezyUpgradeNotes?)

Let us know if you need some help.

---

