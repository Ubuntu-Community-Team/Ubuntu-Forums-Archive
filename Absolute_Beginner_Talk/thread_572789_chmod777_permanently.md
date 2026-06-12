---
title: "chmod777 permanently"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by andydrizen on 2007-10-10
If I want to use virtualBox for my windows-based apps, I have to type

su [enter] [password]
chmod 777 /dev/ blah blah
chmod 777 /dev/ blah blah
chmod 777 /dev/ blah blah


and everytime i reboot, I have to do it again. How do I CHMOD it permanently?

Cheers, 

Andy

---

### Post by HermanAB on 2007-10-10
Try setting the sticky bit.

On the subdirectory do:
$ sudo chmod -R 1777 /wherever/whateverdir

---

### Post by andydrizen on 2007-10-11
didnt seem to work.. :S

---

### Post by jordanmthomas on 2007-10-11
Lazy man's way:
put the chmod commands in /etc/rc.local

---

### Post by andydrizen on 2007-10-13
that worked, thansk :)

---

