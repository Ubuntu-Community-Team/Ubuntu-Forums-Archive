---
title: "Dual Moniter on an ATI card"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2008-02-20
So i have an ATI card, and i have two moniters plugged in. One thru DVI and another thru a DVI-VGA converter. How do i get dual moniters? The built in administration tool doesnt read it. If i try to enable it, it only lets me make it the primary, but even with that its just a clone.

Its an ATI Radeon 9800 XT card

---

### Post by overdrank on 2008-02-20
> **thedrizz said:**
> So i have an ATI card, and i have two moniters plugged in. One thru DVI and another thru a DVI-VGA converter. How do i get dual moniters? The built in administration tool doesnt read it. If i try to enable it, it only lets me make it the primary, but even with that its just a clone.

Its an ATI Radeon 9800 XT card

HI and you may find some help here
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by spiderbatdad on 2008-02-20
There are a number of discussions and how-tos on this. The key is in your xorg.conf file. This may not be the exact thread you need, but you'll get the idea. I don't think the screens and graphics tool in Administration will be of much help.[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by thedrizz on 2008-02-20
oh and im using the nglrx drivers

---

### Post by thedrizz on 2008-02-20
So i followed one of the guides in the first link.

When i rebooted neither screen worked, i had to reconfigure the xorg.conf with the dpkg-reconfigure thing, and now my sound doesnt work.

so :(

the fourth way to do it didnt work at all, and the third screws me up.

Curse you linux!

---

### Post by thedrizz on 2008-02-20
well if anyone wants to help me at least get my sound working again, that would be nice.

Since for some reason it stopped working after i was forced to reconfigure xorg due to the screen not working.

Oh, and this may be part of the problem.

> [QUOTE]ryan@ryan-desktop:~$ sudo aticonfig --query-monitor
[sudo] password for ryan:
  Connected monitors: none
  Enabled monitors: none
ryan@ryan-desktop:~$ 
[/QUOTE]

edit: Fixed sound

---

### Post by thedrizz on 2008-02-21
so does this lack of response mean no one has an answer?

---

