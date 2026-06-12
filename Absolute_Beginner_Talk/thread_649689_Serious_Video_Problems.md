---
title: "Serious Video Problems"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Binary_2 on 2007-12-25
Hi there,
I am not new to Ubuntu, but I certainly not a power user.  I have several machines running Ubuntu at work, but I am trying to revive an oldish laptop.  I downloaded Xubuntu 7.10 and went installing.  Everything went without a hitch.  I booted into Xubuntu off the HDD and everything was fine.  I downloaded security updates and then I installed two "Restricted" drivers.  I installed one for the modem which I don't use, and one for the ATI card on my laptop.  This is of course where all the problems started.  When I subsequently restarted, the machine comes to a blank screen.  If I hit ctrl+alt+F1 the system seems to be kick started and I get some writing on the screen.  No matter how long I wait for the blank screen, the text screen always starts at the same spot when i hit ctrl+alt+F1.  I can then watch the text fly by with what I'm assuming are boot commands and then the screen just goes black again.  I cannot ctrl+alt+F1 anymore, nothing.  Machine is dead.  Any ideas?

---

### Post by candtalan on 2007-12-26
I had slightly similar probs when putting in a restricted a video driver. I subsequently guessed that the driver name in the file /etc/X11/xorg.conf  was maybe wrong for the situation and I tried a simple edit of the driver name (only) in the file - taking it back to the non restriced one's name - and got my display back. I also had had a look at the file contents during running of a live cd, and as it happens I had another install on the same machine in another partiton (which did not use the restricted driver), so I had some choice about how I considered and managed the file contents.
hth

---

