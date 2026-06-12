---
title: "black screen"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by ism. on 2008-04-18
hi. I was just playing around and downloading various things from synaptic and long story short i got into the drivers. One of the drivers was some sort of graphics card for 3D or something like that. Well i restarted and the ubuntu login and desktop screens are black. so i booted into the recovery mode(the command line) and was wondering if anyone had any ideas on what i could do or a command that could help me change the driver back.:(
 
thanks in advanced,
 
-ism.

---

### Post by PmDematagoda on 2008-04-18
You can try:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
also what VGA card do you have?

---

### Post by ism. on 2008-04-18
Thankyou so much Pm!  All fixed with that command! Thankyou Thankyou


-ism.

---

