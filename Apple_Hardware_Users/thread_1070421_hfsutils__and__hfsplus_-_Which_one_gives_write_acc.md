---
title: "hfsutils  and  hfsplus - Which one gives write access ?"
date: 2009-02-15
forum: Apple Hardware Users
---

### Post by stevebush on 2009-02-15
I want the ability to write to HFS+ Journaled partition. Which of the packages: hfsutils OR hfsplus  will allow me to write ?

---

### Post by cyberdork33 on 2009-02-15
> **stevebush said:**
> I want the ability to write to HFS+ Journaled partition. Which of the packages: hfsutils OR hfsplus  will allow me to write ?
neither. Linux does not have the ability to write to a journaled HFS+ partition.

---

### Post by ktran03 on 2009-02-15
is there anyway around this?

I need to edit 2 files on the HFS+ partition, but i can't get into mac because the mouse/key drivers are dead.

---

### Post by cyberdork33 on 2009-02-15
> **ktran03 said:**
> is there anyway around this?

I need to edit 2 files on the HFS+ partition, but i can't get into mac because the mouse/key drivers are dead.
boot from the OSX install dvd. you can use the terminal there, and disable journalling.

---

### Post by ktran03 on 2009-02-15
> **cyberdork33 said:**
> boot from the OSX install dvd. you can use the terminal there, and disable journalling.

when I boot from the cd, I tried to hold down the c key, but it does nothing but restart.

I tried to hold the option key, then selecting the disc, and it just boots normally into os x.

u know how to fix that?

---

### Post by ktran03 on 2009-02-15
just tried the disc on my sisters mac and it works good.

prior to this, I followed this guide

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=480190](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=480190)


maybe i messed something up?

---

