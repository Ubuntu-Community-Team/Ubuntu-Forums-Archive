---
title: "Screen Resolution Problem"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by ebony_rogue on 2007-11-03
I'd had this problem befre, and its pretty irritating since everything is so huge and blurry. Anyway when my brother plays his PC games (on XP, we using dual boot), it changes the resolution on my ubuntu, and its not like he's gonna stop so that I can use the machine. I only have one option under System->Preferences->Screen Resolution: 640X480 and referesh rate of 60Hz. The resolution only changed some time after he had been playing his games, not immediately. Any idea how to solve this one? Thanks

---

### Post by overdrank on 2007-11-03
> **ebony_rogue said:**
> I'd had this problem befre, and its pretty irritating since everything is so huge and blurry. Anyway when my brother plays his PC games (on XP, we using dual boot), it changes the resolution on my ubuntu, and its not like he's gonna stop so that I can use the machine. I only have one option under System->Preferences->Screen Resolution: 640X480 and referesh rate of 60Hz. The resolution only changed some time after he had been playing his games, not immediately. Any idea how to solve this one? Thanks

HI you can reconfigure your xorg. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` In the terminal. Also this page may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Have you installed your drivers for the graphics card? You may check to see if the restricted drivers are enabled under system, administration, Restricted drivers. Hope this helps good luck!

---

