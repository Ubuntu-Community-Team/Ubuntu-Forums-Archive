---
title: "Changing from nvidia to radeon on macbook"
date: 2011-03-09
forum: Apple Hardware Users
---

### Post by tonymartin on 2011-03-09
I installed Ubuntu 10.10 on a Macbook Pro 15" (7,1) without a hitch, but it would not boot the same CD on a Macbook Pro 17" (2,1). 

So I made a copy of the 15" Ubuntu partition and copied it over to the older Macbook. I tweeked a few minor things and got it to boot fairly easily, X and all. However, the text on the display is totally oriented backwards, like mirror image backwards. Top is top and left is left but I need a mirror to read the screen!

I booted up in rescue mode, fixed X (switched from Nvidia drivers to Radeon), ran Xorg -configure and still no change. The login menu is OK, and so are the rescue menus (that asks how you want to fix X).

It seems like this is based on the way the two video cards organize their screen RAM, but I can't figure out what to change in the system to fix it.

If anyone has a clue on how to resolve this I'd love to hear your input.

BTW, this is a 64 bit installation. Works great on the newer 15" system, seems to run fine in console mode on the older machine. Just this one minor issue has got me stumped.

---

### Post by beatskobe on 2011-03-10
The main issue is creating dmg file on another OS (hdiutil).

Does someone know how I can obtain/create a dmg file using ubuntu?

---

