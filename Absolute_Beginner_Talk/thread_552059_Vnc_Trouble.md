---
title: "Vnc Trouble"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by grezer on 2007-09-16
Ok, 

I can VNC just fine or at least I use to, I changed the static IP that I have been using to VNC from my Local Area Connection and the port, when I try to use my Win xp box to VNC to my Ubuntu it works just fine, when I try and do this with my Ubuntu machine though, it acts like its trying to open about 30 to 40 connections all at once and freezes up. 

I belive that I need to kill the sesson, but I am not familar enough with Ubuntu and or linux to do this can some one help ?? 

Thanks

---

### Post by Paul133 on 2007-09-16
Type this in the terminal ```
ps -ef | grep vnc
``` A number should come up along with the vnc program. Then do ```
kill NUMBER
``` where NUMBER is the number on the left, corresponding to the vnc program.

Did that work?

---

