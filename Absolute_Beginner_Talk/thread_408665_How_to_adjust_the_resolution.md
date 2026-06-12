---
title: "How to adjust the resolution?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2007-04-13
I have a running FF Beta on my laptop ACER TM 2493NWLMi. How do I set the native resolution 1280x800 and how do I enable OpenGL rendering?

---

### Post by forrestcupp on 2007-04-13
The first things to try are to go to System->Administration->Restricted Drivers Manager and see if there are any drivers in there for your video card.  If you can enable them, it should automatically give you opengl support, assuming your video card/chip supports opengl.  Next for the resolution, before you try to edit the xorg.conf file, just see if you have the correct resolution listed in System->Preferences->Screen Resolution.

---

### Post by Zdravko on 2007-04-14
The only restricted driver is for my wireless card, I suppose. The only resolution listed is 1024x768. There are no other choices.

---

### Post by Zdravko on 2007-04-14
Bump!

---

### Post by zvacet on 2007-04-14
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

