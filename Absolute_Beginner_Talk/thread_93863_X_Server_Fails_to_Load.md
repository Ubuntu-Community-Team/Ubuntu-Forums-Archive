---
title: "X Server Fails to Load"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by nighthawk39 on 2005-11-22
Hi, I'm pretty new to the world of Linux but I like what I see.  Especially Ubuntu. :)  So far here's my history:

- Knoppix 3.9 LiveCD
- Ubuntu 5.04 LiveCD i386
- Ubuntu 5.10 LiveCD i386
- Ubuntu 5.10 on VMWare Workstation
**- Now I am trying to run the 5.10 LiveCD (64-bit) without success**

My error? **_Failed to start the X server._**  This happens right before Ubuntu should be showing the login screen.

I think it is something to do with my video card, and it's the 64-bit version causing problems becuase:
- when searching for a solution every single topic I found had users with the same series of GFX card (Radeon x700 or above)
- to confirm it wasnt the 64-bit CD causing the problem I tried the 32-bit LiveCD and found it ALSO does not work (I had only used it on an older computer before)

My (new) PC specs:

Pentium D 830 3.0ghz dualcore EM64T (64-bit)
*ATI Radeon X800 GTO 256MB GDDR3 (PCI-e)*
1024MB DDR2 RAM
The motherboad is a 64-bit compatible ASUS, I just don't remember the model right now

The old computer that the 32-bit LiveCD worked on had a P4 2.0ghz, 512 DDR and a GeForce2 mx400 64MB (AGP).

Anything would be helpful!  I am anxious to get this running! :) Thanks.

---

### Post by Brunellus on 2005-11-22
the culprit would be that the live CD does not support your graphics adapter.  

Weird, though, that it doesn't fall back on the usual vesa driver and give you a bog-standard 1024x768 graphics mode.

---

### Post by nighthawk39 on 2005-11-23
[QUOTE=Brunellus]the culprit would be that the live CD does not support your graphics adapter.  

Weird, though, that it doesn't fall back on the usual vesa driver and give you a bog-standard 1024x768 graphics mode.[/QUOTE]
Does that mean the install CD would support my graphics adapter?

Is it possible to enable the VESA driver manually upon loading the LiveCD?

thanks

---

### Post by nighthawk39 on 2005-11-24
Ok, so I managed to get it booted after trying several things, although I had to use VESA moe and it looked really crappy. :( lol I need ATI x800 support! lol

---

### Post by Eoin on 2005-11-27
Hello, I too have an X800 but would really like to ask would there be plans to support this card in the future?

---

