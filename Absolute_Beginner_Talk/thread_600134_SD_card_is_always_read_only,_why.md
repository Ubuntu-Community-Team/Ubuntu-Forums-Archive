---
title: "SD card is always read only, why?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-11-01
On feisty I had no trouble with this, but I have gusty now and for some reason it will only mount my SD card as read only when I stick it in the reader.

---

### Post by Arthur Archnix on 2007-11-02
Have you tried chowning it? Something like sudo chown -R arthur:arthur /media/sda5. Change arthur to your user name, and the path to where the sd card is mounted.

---

