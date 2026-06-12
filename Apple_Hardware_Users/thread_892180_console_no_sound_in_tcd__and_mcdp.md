---
title: "console no sound in tcd  and mcdp"
date: 2008-08-16
forum: Apple Hardware Users
---

### Post by marshag63 on 2008-08-16
Hello!  I just did a fresh install of Ubunto 8.04 on my G4 iMac 800 Mhz.  Following instructions elsewhere on the forum I was able to get sound working (yay), except for with tcd and mcdp (console cd playing programs), however, sound works fine with Music On Console (moc).  What does my cdrom need to play sound?

Any help greatly appreciated!

MarshaG63

---

### Post by Crafty Kisses on 2008-08-17
That's weird, post the following output:
```
lspci
```

---

### Post by marshag63 on 2008-08-17
linux@ubuntu:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
0000:00:10.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth/Pangea GMAC (Sun GEM)

As in the help posts regarding getting sound working I had added "powermac-snd" to /ect/modules

Thanks again for your help!

MarshaG63

---

### Post by youfudoij on 2008-08-17
:guitar:it is an unearthly world. There are all kinds of character. Some of them like promenade. Obtain delight in this far-flung course. Others like assault .fight the enemy. You could find interesting in slow journey.  Step by step. You also could leap in a short time by use safety powerleveling.
[www.8thgame.com](www.8thgame.com) provide safety pl. their gold is cheapeast also.

---

