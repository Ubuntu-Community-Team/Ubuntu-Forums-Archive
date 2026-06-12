---
title: "Removing Graphical Boot"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by esaym on 2006-11-12
I am used to the traditional linux style boot screen with all the text and stuff scrolling faster then you can read.  Anyway I can do away with the normal ubuntu boot splash screen?  I though I saw a topic about this before but now I can't find it:(

---

### Post by aidanr on 2006-11-12
```
sudo gedit /boot/grub/menu.lst
```
and remove the options "quiet" and "splash"

---

### Post by esaym on 2006-11-12
> **aidanr said:**
> ```
sudo gedit /boot/grub/menu.lst
```
and remove the options "quiet" and "splash"
Oh thanks.  Quick question.  /boot/vmlinuz-2.6.15-27-386 root=/dev/hda6 ro quiet splash

What is the "ro" for?  I can't find anything on it

---

### Post by aidanr on 2006-11-12
at a guess i'd say read only

---

### Post by bodhi.zazen on 2006-11-12
Yes it is for read only. The kernel is initially mounted ro.

---

### Post by esaym on 2006-11-12
> **bodhi.zazen said:**
> Yes it is for read only. The kernel is initially mounted ro.
oh so i guess I should leave that part :D

---

