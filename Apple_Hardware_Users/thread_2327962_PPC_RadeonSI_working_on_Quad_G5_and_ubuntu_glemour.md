---
title: "PPC RadeonSI working on Quad G5 and ubuntu glemouregl crash on PPC"
date: 2016-06-16
forum: Apple Hardware Users
---

### Post by luigiburdo on 2016-06-16
Guys i need to notice the RadeonSI boards work on quad g5,
i have tested a Sapphire RadeonHD 7750 (pcie 2.x board)
and it is working in FBdev mode without issue.
But if mesa glemouregl are call from xorg and radeon system freeze with gliches.

I fixed it renaming the glemourgl module of xorg in glemoregl.org 
it made xorg dont open it... in this way you will able to have radeon driver working for 2D accelerations.

Note: The Glamouregl crash in all ppc big endian world 
hope someone will fix it.


Luigi

---

