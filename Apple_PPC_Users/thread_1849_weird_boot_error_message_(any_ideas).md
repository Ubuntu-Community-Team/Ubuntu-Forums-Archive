---
title: "weird boot error message (any ideas)"
date: 2004-10-23
forum: Apple PPC Users
---

### Post by Castaa on 2004-10-23
I'm not sure what this means but it's the first line on my screen when my iBook first begins to boot up.
 
**aty128fb: Invalid ROM signature 8c73 should be 0xaa55**
 
My video cards is a ATI Rage Mobility 128 8MB 2x AGP
 
According to the XFree86 the 'r128' module is loaded for this card.
 
Everything appears to be running fine but I'd like to know what that error means?

---

### Post by muteaid on 2004-10-25
I have the same error.   Should i be passing an argument to the kernel from yaboot?

---

### Post by Biber on 2005-01-23
same for me. Got an iBook 500 dual usb.

---

### Post by Momo on 2005-01-23
Same here with my Radeon.

---

### Post by Castaa on 2005-01-23
Same error with my G3 600Mhz "Dual USB" iBook.  I'm not sure it's causing any problems.  I have no video problems that I know of.

---

### Post by Viro on 2005-01-24
I get that too with my Powerbook (nVidia chipset). No problems though.

---

### Post by bigdufstuff on 2005-09-22
I get this same boot message as well. I am wondering if this should be reported as a bug or not. It doesn't seem to cause any problems but at the same time it looks like a warning or an error that should be fixed. Should I report this?

---

### Post by Ptero-4 on 2005-09-22
[QUOTE=bigdufstuff]I get this same boot message as well. I am wondering if this should be reported as a bug or not. It doesn't seem to cause any problems but at the same time it looks like a warning or an error that should be fixed. Should I report this?[/QUOTE]
 It's a bug that seems to appear in 2.6 kernels and deal with the PPC specific data in those videocards rom. It's mostly harmless but screws HAL/DBUS (this is the one bug that causes the resume-from-sleep issues in these laptops). There's no fix yet but there's a workaround (search for sleep problems or something similar).

---

