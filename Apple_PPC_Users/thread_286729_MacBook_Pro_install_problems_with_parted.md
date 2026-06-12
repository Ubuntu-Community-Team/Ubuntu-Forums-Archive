---
title: "MacBook Pro install problems with parted"
date: 2006-10-28
forum: Apple PPC Users
---

### Post by adam.b on 2006-10-28
I am in the process of installing ubuntu (edgy) on my macbook pro (dual boot). I have followed the directions given <a href="http://ubuntuforums.org/showthread.php?t=198453">here</a>, but I am running into a snag when it comes to setting my sda4 to boot in parted.

I get a response that says, "Unable to open /dev/hda - unrecognised disk label." What am I doing wrong? 

And how might I fix it?

I greatly appreciate any help anyone might be able to give me. :-D

---

### Post by scsimodo on 2006-10-28
> **adam.b said:**
> 
I get a response that says, "Unable to open /dev/hda - unrecognised disk label." What am I doing wrong? 

And how might I fix it?


MacBooks have Serial-ATA HDs, try "parted /dev/sda"

---

