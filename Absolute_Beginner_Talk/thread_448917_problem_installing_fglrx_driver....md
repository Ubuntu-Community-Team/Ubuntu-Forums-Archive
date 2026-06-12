---
title: "problem installing fglrx driver..."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by nealj751 on 2007-05-19
Im using an inspiron 600m laptop w/ an ATI mobility radeon 9000 32mb
and have been using this guide to install the fglrx:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
when i restart x after editing xorg.conf i get an error w/ xorg.conf saying its most likely not set up correctly.
i've tried modifying the xorg.conf numerous ways.  anyone know if there's a compatibility issue w/ my video card?

---

### Post by Bachstelze on 2007-05-19
> Prerequisites

Make sure the following things are true about your video card:

    *      It is a 'Radeon' card
    *      The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. **The 'fglrx' driver does not support cards earlier than the 9500.**


You get the point ;)

---

### Post by nealj751 on 2007-05-19
aww schucks.

---

### Post by Game_Ender on 2007-05-28
Install version the [8.28.8]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") version.

---

### Post by nealj751 on 2007-06-03
when i try to install it i get this:
./ati-installer.sh: 165: Syntax error: Bad substitution

---

