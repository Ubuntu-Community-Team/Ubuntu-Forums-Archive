---
title: "Two black bars (cursor) on screen"
date: 2007-11-11
forum: Apple PPC Users
---

### Post by Dummy00001 on 2007-11-11
I have weird problem. Check attached screen shot: two black bars appear on top of otherwise bluish screen. When window gets into the screen position, its content gets painted by the black bars like brushes. Sometimes it looks very messy, since all new windows appear at top of screen and their titles get polluted.

This is on newworld PowerBook G4 12" @ 1GHz with nVidia graphics:
0000:00:10.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)

Non-scientific tests have established that it is in fact a cursor on /dev/tty7 - where Xorg is attached.

Does anybody knows how to fix that?

---

### Post by Pokefan on 2007-11-16
bump...

Same Issue here in the exact same spots on same PB

---

### Post by ian.jpg on 2007-11-17
I have a similar problem on my iBook G4.  Although the black bars are static and don't effect any of the windows.  They just sit at the top of the screen.  They weren't there in Feisty.

---

### Post by spudw on 2007-12-23
i had the same problem til i changed the default depth in my xorg.conf to 24 instead of 16 :)

---

