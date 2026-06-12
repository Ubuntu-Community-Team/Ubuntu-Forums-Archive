---
title: "Monitor does not work on ubuntu"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by jonaslc on 2006-04-20
I just switched to ubuntu but my monitor does not work with it correctly with it.  I can get to the login screen now but after that I cannot see anything.  If I use the monitor on a windows system it works fine.  And it worked before but now I do not know what happened.  can anyone help me?

---

### Post by gondilon on 2006-04-20
does the problem happen if you are at a text console? In case you don't know, to get to one press ctrl-alt-backspace at the login screen.

---

### Post by nsmith on 2006-04-20
I cannot get to the login screen now.  It is all black.  I can hear load though.  I can hear the Ubuntu drum beat.  I tried doing sudo dpkg-reconfigure xserver-xorg as seen in a thread by nsmith
it would seem we have the same problem.

---

### Post by nsmith on 2006-04-20
sorry I just confused myself with myself

Jonaslc it seems we have the same problem

---

### Post by nsmith on 2006-04-20
try this
I have had luck in the past with this but not this time

sudo dpkg-reconfigure xserver-xorg

Fallow the instructions on the screen it will ask you a bunch of questions about your hardware.  If you do not know the answer leave it blank or just hit enter.  When you get to the monitor part.  Autodetec and then answer the questions and select your screen resolution.

Good luck

---

