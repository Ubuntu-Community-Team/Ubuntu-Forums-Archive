---
title: "can't login to ubuntu"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ngeleven on 2008-01-08
I can't login to ubuntu becuase i change the option in login window (system->administration->log in window).

on the security tab, i check the option "enable time log in " and the user name is my username. time log in is 30 sec but i don't check the option "Automatic Login".

next time, i login it appear a black screen and an aminate round cursor. i try to wait it for a long time but nothing to happen.

i use ubuntu v7.04

can anyone help me on this problem?
:(

---

### Post by Hospadar on 2008-01-09
try doing a ctrl-alt-backspace at the login window, It should reload X causing you to get a non-timeout-ed login window.  if that doesn't work, try going to a text terminal (ctrl-alt-F1) and then killing your x/gdm session with ```
sudo /etc/init.d/gdm stop
``` and then starting directly into Xwindows with ```
startx
```(avoiding the graphical login manager) from there you can change your setting for auto-login

---

### Post by ngeleven on 2008-01-09
I have tried your code but it doesn't work. 
first i try to use CTRL + ALT + F1, type the log in name and password. next i type "sudo /etc/init.d/gdm stop and then i type "startx" but the problem is still happened.
it appear that " Disable GNOME Manager"  

can you give me more comment?

---

