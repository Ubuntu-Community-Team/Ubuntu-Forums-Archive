---
title: "Cant install libsdl-dev"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by zlgo on 2007-03-22
Hi, iv recently installed edgy eft ubuntu but now that i want to develop, i cant install libsdl1.2-dev. The reason for this is that it has a depends on libglu1-mesa-dev.
i.e:

libsdl1.2-dev:
 Depends: libglu1-mesa-dev but it is not going to be installed or
	libglu-dev

 and when i try to install libglu1-mesa-dev i get:

libglu1-mesa-dev:
  Depends: libglu1-mesa (=6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed

I have libglu1-mesa already installed, i have an ATI Radeon X1600 graphics card, ati drivers installed already but i cant install libsdl-dev!

---

### Post by Bachstelze on 2007-03-22
You installed libglu1-mesa from a non-official repo. Ask the people who run it to provide you a compatible libglu1-mesa-dev.

---

