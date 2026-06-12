---
title: "Blackout after power cable comes out (MacBook Pro)"
date: 2010-12-23
forum: Apple Hardware Users
---

### Post by Symbolix on 2010-12-23
Hi,
A MacBook Pro here (1151A, 1,2?, anyway a 2006 model).
Ubuntu 8.04

When the power cable comes out, the laptop blacks out. I mean, it kind of goes into sleep mode, but only with the screen going dark. Anything running keeps running.

I know it is a bug, and I did my homework. I researched it. It usually comes to the point where you need to disable an "event" on "power cable out" in the power management settings of gnome. I did that, but the problem is still there.

I was turning off the computer before, loosing all my work, because there is no way to bring the display back. However recently I discovered two work arounds:

1) Restart X server: CTRL+ALT+BACKSPACE (you loose stuff)
2) FN+CTRL+ALT+F7 which takes you back to your desktop, you do not loose anything.

So any ideas about that? And please do not tell me to upgrade to 10.04 etc. I can not, long story! :)

Thanks.

---

### Post by kwiksand on 2010-12-23
Can't you just turn the brightness back up? (F2 or Fn+F2)

If that doesn't work, make sure pommed and the bl-dkms packages are installed correctly.

Note: It happens on mine too (and possibly dims too much, I'm sure this can be configured somewhere), but its very simple to adjust the brightness if its too dark!

---

### Post by Symbolix on 2010-12-26
Well,
I do not think it is a brightness-dimmimg issue. If there is video playing or music playing and I pull the cable... it goes blank... i can still hear the video or the music, which makes it look like it is dimmed down, but nothing helps except FN+CTRL+ALT+F6 and then FN+CTRL+ALT+F7 and then i can see my stuff again. :(

I have installed pommed despite the fact all keys were working. Not sure if this helped.

---

