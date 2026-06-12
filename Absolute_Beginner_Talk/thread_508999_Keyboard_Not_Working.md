---
title: "Keyboard Not Working"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by fattom23 on 2007-07-24
Is there a reason that you know of that a keyboard would work using one kernel but not another?  Don't both kernels use the same xorg.conf file?  When I boot up the 2.6.17-12-386 kernel, my keyboard works fine.  I would like to use the 2.6.17-12-generic kernel (to enable dual core support), but my keyboard won't work when I boot the kernel.  What are some things that could be causing the difference?  At least a point in the right direction would be helpful.  Thanks a lot in advance for any help you can offer.

---

### Post by Paul S on 2007-07-24
Take a look in /var/log/Xorg.0.log to get a clue, after booting into the kernel that doesn't work.

---

### Post by fattom23 on 2007-07-24
How can I check the contents of that file if my keyboard doesn't work?  I can get to the Ubuntu login screen, but the keyboard won't work after that point.  I can't even enter one letter of my login.

---

### Post by Paul S on 2007-07-26
> **fattom23 said:**
> How can I check the contents of that file if my keyboard doesn't work?  I can get to the Ubuntu login screen, but the keyboard won't work after that point.  I can't even enter one letter of my login.

Xorg keeps the current as well as the previous Xorg.0.log file.  The previous one is Xorg.0.log.old.  Therefore, log in first with your bad kernel to create a log file with the failed messages, then log in with your working kernel.  Now the Xorg.0.log will have the information for the working system and the Xorg.0.log.old will have the prior failed startup.  Compare these two files to find the error that's preventing your keyboard from starting.

You can use "diff /var/log/Xorg.0.log /var/log/Xorg.0.log.old" in a terminal to show just the differences, but you probably want to open both documents in an editor and have them side by side.  When you find the failed message, try putting it in a google search to see if a solution is already found by some other user.

HTH,

---

### Post by fattom23 on 2007-07-26
Thanks a million.  I've since "fixed" my system such that it's required a complete re-install, but I'm really glad that I know that now!  Peace!

---

