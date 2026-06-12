---
title: "Simple issues/questions with applications/adding"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by diizy on 2007-10-19
Hi All,

I love this os! but anyways, i am working into music editing, so there are a couple in that area.

When I try to load "freewheeling" from the application menu, it does not load. Is there another way to launch this program?

Ardour will not select in the "add/remove" menu. The box is grey, i'm not sure here.

Otherwise, thanks for any assistance!

---

### Post by tzulberti on 2007-10-19
Try to open a console and type "freewheeling". It should appear some message and see if it open.

---

### Post by davidjmayo on 2007-10-20
> Ardour will not select in the "add/remove" menu. The box is grey, i'm not sure here.


in a console do

```
sudo apt-get update
```

then go back to add/remove and see if it white (available)

---

### Post by diizy on 2007-10-20
[QUOTE=davidjmayo;3576816]in a console do

```
sudo apt-get update
```

then go back to add/remove and see if it white 

Hmm I tried this, although the box just stays grey

---

### Post by barkej on 2007-10-20
Goto System>Administration>Software Sources. Make sure you have Universe and Multiverse enabled. Then try installing Ardour and see how that works.

---

### Post by diizy on 2007-10-20
> **barkej said:**
> Goto System>Administration>Software Sources. Make sure you have Universe and Multiverse enabled. Then try installing Ardour and see how that works.

dude, thank you for unintentionally pointing out something else excellent - Synaptic pacakage manager.. I will simply get it from there. thanks :P

very impressed by this os this far! i have everything i had before with exclusion of windows editing programs, which can still be run in wine... :P

---

