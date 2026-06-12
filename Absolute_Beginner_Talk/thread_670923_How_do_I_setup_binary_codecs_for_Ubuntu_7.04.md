---
title: "How do I setup binary codecs for Ubuntu 7.04?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by sundar22in on 2008-01-18
I would like to setup the following in Ubuntu 7.04 machine:

* Mp3 support for mplayer
* wmv support for mplayer
* Flash player
* rar file support
* Chm file viewer


Thank you.

~ Sundar ~

---

### Post by mattismyname on 2008-01-18
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That should work for mp3 & wmv.

Flash -> Just search in Synaptic for Adobe's flash player.

rar -> sudo apt-get install rar

chm -> Google "chm file viewer in linux".  Seems there are a few options you can try such as kchm.

---

### Post by jleaker01z on 2008-01-18
Use your add/remove programs under applications.  Search for 'flash' and select Macromedia Flash Player, then search for 'gstreamer' and you will find all the codecs you need

---

### Post by jleaker01z on 2008-01-18
> **mattismyname said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


chm -> Google "chm file viewer in linux".  Seems there are a few options you can try such as kchm.

I would google 'ubuntu chm viewer' myself ;)  If you can find it in a .deb package it makes installation alot easier.  I started out searching for 'linux' items, but after a few times of beating my head against a wall trying to install something, only to figure out later that there was another program that the package manager would install for me, I started to specify Ubuntu or 'debian'.

---

### Post by jeffus_il on 2008-01-18
Here is a thread with a howto:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by mattismyname on 2008-01-18
jleaker:

Yeah, I suppose.  I usually use Linux to ensure the broadest search and once I find the app I like best I'll see how well Ubuntu supports it.

---

