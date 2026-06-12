---
title: "What is this &quot;DVD&quot; thingamajig?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-09-30
I was just wondering why Linux doesn't let me play DVD's, or watch any sort of videos.  Is there some kind of software that I need to make it possible?

---

### Post by K.Mandla on 2006-09-30
Encrypted DVDs (like the ones you get from Blockbuster) will need a little attention to get started.

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by Marsolin on 2006-09-30
Some proprietary codecs and decryption are sometimes needed. Here are some packages that you should install. Hopefully the two of them will clear up your problem.

[libdvdcss2]("http://linuxappfinder.com/package/libdvdcss2")
[w32codecs]("http://linuxappfinder.com/package/w32codecs")

Note that libdvdcss2 technically violates the DMCA in the US because of is breaking copy protection on the DVD, although many people use it anyway.

---

### Post by Atomic Dog on 2006-09-30
This link will tell you everything about restricted formats and how to download all the drivers you'll need.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

