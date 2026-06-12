---
title: "mounting macosx partition on ubuntu"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by phenix on 2006-03-19
I was just wandering is there was anyway that I could mount my macosx partition on ubuntu 

thanks!!!!

---

### Post by rado_london on 2006-03-19
Hi I dont know about the mac os x partition but can you tell me what extention it is because I am curious.

---

### Post by phenix on 2006-03-19
Mac OSX Extended (Journaled) HSF

---

### Post by pranith on 2006-03-19
hi,
code:[COLOR="Red"][B]
mkdir /mnt/mac
mount -t hfsplus /dev/sdaX /mnt/mac (change /dev/sdaX with your HFS+ partition)[/B][/COLOR]

you might want to install hfsplus using synaptic or apt....

---

