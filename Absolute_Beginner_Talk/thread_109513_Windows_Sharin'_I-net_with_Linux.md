---
title: "Windows Sharin' I-net with Linux"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by Protoman on 2005-12-28
Unforunatly since my WPC54GX isn't going to be supported under 5.10 anytime soon, I need my XP PRO box to share with my Linux laptop.  Windows to Windows I can do,  Linux providing to Windows I can google up right away, Windows sharing I-net to Linux is something I can't do and google up either.  Currently my XP box  and Linux machines are connected, with a crossover cable, by their 10/100 Ethernet cards.

---

### Post by Chipmunk on 2005-12-28
If you enable internet connection sharing in the XP box, and connect the linux laptop direct (as you have now), Ubuntu should pick up an IP address from the XP box (probably in the 192.168.0.x range) and you should be online just fine. Ethernet should be independant of the operating system, the xp box will just see a new host appear on the end of the cable and hand it an IP.

---

