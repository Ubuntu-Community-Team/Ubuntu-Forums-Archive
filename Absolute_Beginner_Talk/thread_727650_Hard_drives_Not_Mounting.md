---
title: "Hard drives Not Mounting"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by GB56 on 2008-03-18
I am a first time Linux/Ubanu user - so I am not how to psoe this question.

I have a Feisty Live CD, and when booting up is finds both my hard drives without a problem, recently I got a Live CD of Gutsy - when booting with it, the hard drives are not accessible by Gutsy. They can be seen but not accessed.

Appreciate any learning I can get.

TIA

GB

---

### Post by kpkeerthi on 2008-03-18
Can you post the output of
```
sudo fdisk -l
```
This will list all partitions seen by gutsy we may need to manually mount.

---

