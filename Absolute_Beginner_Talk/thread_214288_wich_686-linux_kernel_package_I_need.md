---
title: "wich 686-linux kernel package I need /"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-12
I want to make ubuntu faster
I have pentium4 1800Mhz and 1GB RAM

it has been said that I need to get the metapack linux kernel
in the advanced add/remove there are dozens of 686 packages
wich one do I need ? give me the excact name please...

---

### Post by Sonic Alpha on 2006-07-12
Does your P4 have HT? (Hyper Threading)

---

### Post by fluffington on 2006-07-12
linux-686

Edit: that assumes single-core. It's linux-686-smp if you have multiple cores/processors.

---

### Post by MaximB on 2006-07-12
thanx - I've installed it
but why now do I have bout 386 and 686 linux kernels ???
do I need to remove the 386 kernel ?
how they are working together ?

---

### Post by az on 2006-07-12
Unless you boot the 386 kernel, you are not running it.  You get the option to boot any kernel you have laying around your system at boot time, from the grub menu.

You can remove all of the 386 linux-images if the 686 is working fine for you.

---

### Post by NT4usB on 2006-07-12
> **azz said:**
> Unless you boot the 386 kernel, you are not running it.  You get the option to boot any kernel you have laying around your system at boot time, from the grub menu.

You can remove all of the 386 linux-images if the 686 is working fine for you.

I was wondering about that myself. After the latest update, I'm out of room on /, or /root, or /boot, or whatever partition (not in front of the box atm.)
I have 23-386, 23-686, 25-686, and 26-686 (maybe more...)
I'd like to nuke a couple anyway, just to free up some space.
Can I be sure nothing I have running on 26-686 depends on them?
I understand about keeping one to fall back on if I whack the current one. nbd for me though, it's strictly a PVR and I can rebuild it from scratch in a few hours if I break it.

---

### Post by az on 2006-07-12
Yes you can remove them.  There is a spec for automatic kernel removal.  Maybe it will get done for Edgy.

---

### Post by NT4usB on 2006-07-12
Thanks. I'll remove them tonight.
[Do you ever go to Les Régates de Valleyfield?]

---

