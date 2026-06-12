---
title: "Can I install Xubuntu at the Ubuntu liveCD boot menu?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-04
Can I install Xubuntu at the Ubuntu liveCD boot menu?

---

### Post by rionoco on 2006-11-04
which graphic card do u have?

---

### Post by tuxcantfly on 2006-11-04
no, you'll need the alternate install cd to do that. you can, though, boot up xubuntu in live mode and install it with the installer

---

### Post by rionoco on 2006-11-04
and...yes u can

---

### Post by rionoco on 2006-11-04
if you go into the safe graphic mode..there is an option in the desktop (install)

---

### Post by lordvolo on 2006-11-04
how do I install from the boot menu?^^^

---

### Post by lordvolo on 2006-11-04
> **rionoco said:**
> if you go into the safe graphic mode..there is an option in the desktop (install)

will this xubuntu from the ubuntu liveCD?

---

### Post by rionoco on 2006-11-04
put in the cd....restart computer,
press F2 before intiate your operational system.
go to the option boot
and change the boot priority to the cd...save changes and thats it

that answer you question??:-k

---

### Post by caravel on 2006-11-04
> **lordvolo said:**
> will this xubuntu from the ubuntu liveCD?

You cannot install **X**ubuntu from the Ubuntu livecd.  Just install Ubuntu from the livecd and then do:

sudo apt-get install xubuntu-desktop

This will instal the Xfce desktop manager, effectively giving you Xubuntu.  Whe you log in just change the session type to Xfce.

---

