---
title: "Desktop gone?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-11-18
I have just updated Feisty to Gutsy, overnight as it was so slow, and my desktop has gone! The menu bars are there but with a blue screen in the middle!
Clicking on places/home or desktop produces nothing.
Any ideas if I can correct this without another long upgrade and losing my work in the process?

---

### Post by bigken on 2007-11-18
try booting into safe mode and type

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install ubuntu-desktop

---

### Post by Benbow on 2007-11-18
I had to do a dpkp --configure -a first and then I followed your instructions above but I still have no desktop.
Looks like I will have to do a complete reinstall unless there are any other ideas out there?

---

### Post by shoaibi on 2007-11-18
sorry to ask an ir-relevant question:
isn't there a way to un-install the last update?

atleast its possible incase of a kernel update, i don't know about other things...

---

### Post by bigken on 2007-11-18
try this

sudo apt-get dist-upgrade

---

