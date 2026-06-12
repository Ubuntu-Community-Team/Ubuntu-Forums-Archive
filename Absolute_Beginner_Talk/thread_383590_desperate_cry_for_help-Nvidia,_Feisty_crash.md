---
title: "desperate cry for help-Nvidia, Feisty crash"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-03-13
Please help, I'm at my wits end.

I got Edgy up and running nicely problem was it wouldn't mount my wifes iPod.  (I use the computer for media stuff and would rather not assist a monopoly)

Someone suggested I try Feisty.  I did and I liked it.  The iPod nano Raid/Hal issue has cleared up/been fixed.

I messed about with themes and even got Compiz working with the addition of adding some extra code to get cubes and window edges.

Today I downloaded 140 odd upgrades and now on startup I am told:
"error running install command for nvidia kernel module"

I have tried reconfiguring the xserver-xorg to no effect

I have tried sudo aptitude install nvidia-glx to be told nothing needs fetching.

I am new to all this what should I do?

---

### Post by userundefine on 2007-03-13
Feisty is alpha software and should not be relied upon for your main OS.  Your question would be better suited for the Feisty forum.

---

### Post by dgeorgester on 2007-03-22
I had the same problem. I fixed mine by updating my restricted-modules package.
Check this link:
[http://ubuntuforums.org/showthread.php?t=376836]("http://ubuntuforums.org/showthread.php?t=376836")

Just install the correct modules using apt.

---

