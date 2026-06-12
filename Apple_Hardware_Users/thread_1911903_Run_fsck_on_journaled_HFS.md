---
title: "Run fsck on journaled HFS"
date: 2012-01-19
forum: Apple Hardware Users
---

### Post by T-bone24 on 2012-01-19
Hey, I've been having problems booting my iMac, booting it in verbose mode I can see a message about running fsck on my hard drive (the message appears very briefly before the machine turns it's self off) for some reason it can't even boot into by external hard drive with OSX on it, nor a Snow Leopard installation dvd, it can however, boot into a Natty live cd.  I've installed hfsprogs but the hard drive with osx on it is unfortunately journaled so I'm unable to run fsck on it. Does anyone know any way I can run fsck on a journaled disk or somehow disable journaling through ubuntu?

Also, I have a macbook to hand, it's a long shot, but I was wondering if it there's a way I could run fsck from the macbook and somehow target the iMac's disk via ssh to ubuntu running on the iMac?

---

### Post by allebone on 2012-01-20
Doesnt sound good. Did you test the hard disk for failure?

---

