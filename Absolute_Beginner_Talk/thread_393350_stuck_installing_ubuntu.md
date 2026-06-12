---
title: "stuck installing ubuntu"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by iPirates on 2007-03-25
I have Kubuntu installed on my computer, and it's running great.  My problem is trying to install Ubuntu on my friend's computer (I'm slowly convincing him to try out ubuntu!), and the liveCD appears to load properly (ubuntu loading screen appears fine), but once we hit the desktop, it never actually shows the desktop.

All we get is a ton of funky-colored, vertical lines.  From what I can see the computer's responsive, because the vertical colors change color when i try moving the mouse around and clicking at random.

I tried the alternate install CD, thinking that liveCD was to blame, but when we got Ubuntu loaded up, and tried logging in, the same problem occured (at the login screen).

His computer specs are:

AMD Sempron 32bit 2.0 ghz processor
512 ram
nVidia 6600 (evga drivers or something?)

I think that the video card is to blame.  I have the same one, except it's the over clocked version, and made by BFG, and mine works fine.  

Other then that, i'm stuck... any ideas?

---

### Post by monkeyking on 2007-03-25
have you tried running safe mode ?

---

### Post by jeffathehutt on 2007-03-25
Does you friend's computer run Windows without any problems?  It's unlikely to happen but maybe the video card is not seated all the way into the slot.

---

### Post by iPirates on 2007-03-25
yea, safe mode produces the same results.
and windows runs without any problems, but i hadn't thought of that one...

---

### Post by jeffathehutt on 2007-03-25
What version of Ubuntu are you trying to install?  I see you tried both the desktop and alternate cd, so you can pretty much rule out a bad cd.  If you are trying to get edgy to work, try dapper and see if that gives better results.

Also, you could try booting into Ubuntu again, and when the screen gets messed up, hit Ctrl-Alt-F1.  That should give you a terminal where you can login.  If the terminal works, try editing /etc/X11/xorg.conf and change the video driver to vesa.  Reboot and see if that makes a difference.

---

### Post by iPirates on 2007-03-25
hey thanks, i'll give that a shot...

---

