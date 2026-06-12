---
title: "Help, display all garbled"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by BattleGnome on 2007-11-02
I just finished installing ubuntu 7.10 on my dell inspiron 6400 and I noticed I was stuck in 1024*768. SO I decided to manually change the resolution to 1280*800 through the screens and graphics app. Now my ubuntu desktop is completely garbled and I cannot see anything. How do I restore?

---

### Post by Adramelech on 2007-11-02
Boot into recovery mode and type:

sudo dpkg-reconfigure -phigh xserver-xorg

---

