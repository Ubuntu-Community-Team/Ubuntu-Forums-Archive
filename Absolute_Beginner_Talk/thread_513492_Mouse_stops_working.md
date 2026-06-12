---
title: "Mouse stops working"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Roger D on 2007-07-30
Hi

I'm running Dapper on a fairly standard system -
  Processor: AMD Athlon 3200+
   Memory 1024MB DDR2 667Mz     
  Motherboard: Asus M2NPV-VM 
   Navidia GeForce 7300 LE graphics card

Generally works fine, but every now and the  the mouse pointer stops working - I can move it around the screen, but when I click on an icon, nothing happens. An earlier posting on this problem suggested that my Microsoft Wireless mouse might be the problem. I switched back to a wired PS/2 mouse, and while all was well for a few days, the old problem has come back. Ctrl, Alt, Backspace ,to re-start X, is one solution, but I also find that using the keyboard to shift to another desktop, and then shifting back again,  so far at least, solves the problem.

OK, I can live with this, but it isn't the way a rock-solid, desktop-ready OS is meant to behave.

Does anyone have any ideas for getting to the bottom of what's wrong with my mouse?

Best regards

Roger Dettmer

---

### Post by compiledkernel on 2007-07-30
Odd. Hrmmm ok. 

If restarting X solves the problem then I assume that something in your Xorg log will show the issue. 

cat /var/log/Xorg.0.log > ~/xorg.txt 

Thatll create the xorg.txt into your home directory, then post the last 100 or so lines of it here (preferably at the time the error occurs/occured).

---

### Post by freesitebuilder on 2007-07-30
I've had mouse problems, which have been added to the Launchpad here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194)

However it doesn't sound like the same problem - you could do a search on Launchpad to see if anyone else has reported it, or to add it.

---

### Post by Roger D on 2007-07-30
> **compiledkernel said:**
> Odd. Hrmmm ok. 

If restarting X solves the problem then I assume that something in your Xorg log will show the issue. 

cat /var/log/Xorg.0.log > ~/xorg.txt 

Thatll create the xorg.txt into your home directory, then post the last 100 or so lines of it here (preferably at the time the error occurs/occured).

Many thanks for the suggestion. When it happens again, I'll do another post with the Xorg log

Roger D

---

