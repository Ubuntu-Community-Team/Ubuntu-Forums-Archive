---
title: "Microphone not working properly"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by nik62790 on 2007-11-22
I just recently purchased a mic for my computer and when i run a program that uses it such as fmit or the sound recorder it dosent seem to pic up any sound and if it does its extremely quiet.  I've tried turning up the mic volume and the front mic volume and nothing i do seems to be working.  when i tried using it in windows it worked just fine.. please help me. i dont want to have to use windows.

---

### Post by dboyd13 on 2007-11-22
I'm not at by ubuntu machine to give you the exact instructions... but you can try this:

Open a terminal and type:
alsamixer
Use the arrow keys to highlight "Mic Boost" and press "m" to turn it on.

---

### Post by ugm6hr on 2007-11-22
> **dboyd13 said:**
> I'm not at by ubuntu machine to give you the exact instructions... but you can try this:

Open a terminal and type:
alsamixer
Use the arrow keys to highlight "Mic Boost" and press "m" to turn it on.

```
alsamixer
```
As above - and use the Tab button to go to the "Capture" settings, and make sure the correct inputs are set.

```
amixer
```
This can sometimes allow access to commands that alsamixer doesn't.

---

