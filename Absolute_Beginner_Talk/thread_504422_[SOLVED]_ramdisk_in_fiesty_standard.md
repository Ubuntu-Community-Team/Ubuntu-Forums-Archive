---
title: "[SOLVED] ramdisk in fiesty standard"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-07-19
does fiesty fawn come standard with a ramdisk be it static or dynamic in size.if so how do you access it.thanks

---

### Post by mjwhitfield on 2007-07-19
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

I hope that helps, I've not tried it.

---

### Post by stinger30au on 2007-07-19
thanks i will have a go

---

### Post by stinger30au on 2007-07-22
found this

Ubuntu and Debian auto-mount a ramdisk using tmpfs. This gets mounted to /dev/shm and is usable by anyone (just cd to /dev/shm and start plonking files in there).

the ram disk is dynamic, not static (resizes automatically and will use up to half your available ram)

---

