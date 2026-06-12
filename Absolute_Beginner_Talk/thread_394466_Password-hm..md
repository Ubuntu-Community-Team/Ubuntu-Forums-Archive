---
title: "Password-hm."
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-03-26
So I couldn't su my terminal today using the usual password-Hmmmmm. That's interesting. So how do I change the password? The help search brought up irrelevant results and I tried looking through the various menus but couldn't find it..

Edit: that is, I couldn't SU my terminal. Not to say I couldn't open it, of course.

---

### Post by devnulljp on 2007-03-26
Sure you don't have capslock on or something?
anyway, boot into safe mode, then reset your user password
passwd <username>

---

### Post by Aurora Borealis on 2007-03-26
Thank you for your reply. Yes-I checked the caps and they're off. How do I boot into safe mode? (I'm the ultimate newbie.)

---

### Post by Aurora Borealis on 2007-03-27
Well, I finally figured out how to square everything away. I changed the password and wouldn't you know-not two hours later it had been changed again. I suspect a kid with too much time on his hands and not enough chores around the house. Did a clean install-guess it's the only way to truly trust my system again.

---

### Post by devnulljp on 2007-03-29
> **Aurora Borealis said:**
> Thank you for your reply. Yes-I checked the caps and they're off. How do I boot into safe mode? (I'm the ultimate newbie.)
Reboot and in the GRUB menu choose the entry that looks something like this:
```
Ubuntu, kernel 2.6.15-28-386 (recovery mode)
```
Or, in a console type init 1, which will dump you into single user mode. From there you should be able to fix things.

I just read your next post, you reckon you were owned? Not nice. Here's some precautions to stop it happening again. Are you the only user on the box? (must've been a real dumb hacker to change your password and alert you).

Set a good password, at least 8 characters, mix upper/lower case, no dictionary words, include upper characters (!"£$%^&*-+*_#/?\), disable the root account, prevent root logging in through ssh (turn it off completely if you don't need it), try bastille to harden the machine, use pam_abl or denyhosts to stop dictionary attacks.

---

### Post by Aurora Borealis on 2007-04-01
Awesome! Thank you very much!

---

