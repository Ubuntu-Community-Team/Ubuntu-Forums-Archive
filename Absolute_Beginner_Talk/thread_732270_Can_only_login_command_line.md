---
title: "Can only login command line"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by IlMadCowlI on 2008-03-22
I am running 7.10 gusty and I can't get into the GUI.  I have had this problem for a while now and have just let it sit.  I don't remember what i was doing when my xserver crashed but I am running 3 different computers with ubuntu and never ran into this problem.  I have tried to configure xorg.config over again and nothing happened.

---

### Post by tvtech on 2008-03-22
what happens when you try to manually start GDM ?

---

### Post by dansco on 2008-03-22
i still new to ubuntu myself but try this code

sudo dpkg-reconfigure xserver-xorg

hope it might help

---

### Post by IlMadCowlI on 2008-03-22
when i try to start it manually it fails.

---

### Post by IlMadCowlI on 2008-03-22
I tried the sudo dpkg-reconfigure xserver-xorg and that didnt work either the only thing i can do is login through the terminal login it says "kinit: trying to resume from /dev/disk/by=uuid/2fc0baaf-1dac.....
kinit: No resume image, going normal boot

---

