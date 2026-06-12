---
title: "HELP! Ndiswrapper DWA 552 Modprobe crashes"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Bender 3000 on 2008-04-08
Hi I have tried just about everything. From re-installs to different Ndiswrapper versions and everytime I go into the last step the modprobe command it freezes and does'nt do anything different upon reboot I am only able to install the driver not start Ndiswrapper. I have also tried multiple tutorials and none of them seem to help, I am running Ubuntu 7.10 32 bit the driver from the CD as recommended on the compatible cards list and the ndiswrapper off the ubuntu disk (1.43). thanks

---

### Post by dstew on 2008-04-08
What kernel do you have?```
uname -r
```You might have to compile a newer ndiswrapper version directly from the source code to get it to work with your kernel. If it crashes with modprobe, it is likely that the ndiswrapper version is too old, or has bugs in it (relative to your hardware).

EDIT: Regarding compiling from source, the best thread I have seen on that subject is [here]("http://ubuntuforums.org/showthread.php?t=476523&page=3"). Good links, expert advice, and a persistent user who was eventually successful. The main issue is completely removing all traces of previous ndiswrapper installations, both from synaptic, and from the compiler.

---

### Post by Bender 3000 on 2008-04-08
Thanks for the help man. But I couldn't get it to work because I'm a n00blette.:lolflag: I'm just gonna get a wireless card on eBay with a native driver worked all day & part of the night.

---

