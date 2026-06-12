---
title: "[SOLVED] Unable to boot windows after Gutsy upgrade"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-10-20
OK, I know this should be something simple, but I just can't seem to get it.  I just upgraded from Feisty to Gutsy using the upgrade button.  I can't boot into Windows now.  I know I have to change menu.lst, but I just can't seem to get that right.  Windows is on /dev/sda2.  The entry in menu.lst for my windows partition is

title  Windows
root  (hd0,2)
makeactive
chainloader

I had this working just fine dual boot with Feisty.  But the upgrade changed my menu.lst, and I entered the above.  When I try to boot into windows, I get error 13: invalid or unsupported executable format

How to fix this?

---

### Post by dndrich on 2007-10-20
OK, I solved my own problem.  Turns out Windows is on (hd0,1).  Editing that solved it.

---

### Post by Maestro23 on 2007-10-20
Good deal man.  Can you mark this SOLVED using the Thread Tools.  Thanks. :)

---

