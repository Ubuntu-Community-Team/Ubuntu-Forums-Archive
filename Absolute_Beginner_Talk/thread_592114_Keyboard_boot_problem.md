---
title: "Keyboard boot problem"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ColinT on 2007-10-26
Hi All

Running 7.04 for a few months now. Eat your heart out Bill Gates!

Just bought an Advent lazer / USB wireless keyboard and mouse (using it now). All works fine except for boot.

I have a BIOS password which I can enter from the keybd. Next screen is dual boot - Ubuntu and XP. No keys work to allow me to scroll up or down the list therefore it times out and loads Ubuntu. 

If I connect my old keyboard it works fine. Puzzled because the KB is obviously being recognised  at BIOS level. Works fine in Ubuntu as you can see. By the way, mouse works fine.

Grateful for any guidance / help on this. Keep up the good work!

Regards

Colin

---

### Post by Trebaruna on 2007-10-26
Aside from being able to punch in your BIOS pass, have you enabled USB keyboard in the BIOS settings? Maybe an obvious point, but it could help. If it only provides keyboard for itself, and then later when Ubuntu loads it picks it up as well, then GRUB is left hanging...?
In my BIOS at least I have the option to enable USB keyboards and mice.

---

### Post by ColinT on 2007-10-27
Thank you for the reply.

I don't appear to have a KeyB USB enable function within my BIOS. Using two keyboards to get around the problem at the moment anyway.

Regards

---

### Post by Mike Armstrong on 2007-11-04
Look for the older / legacy USB support option in the bios and enable ... it worked for me!
Now I can boot into Ubuntu or Windoze XP at will.
Cool!

---

### Post by ColinT on 2007-11-05
Thanks now sorted. USB support was disabled - I just couldn't see it. Moral of the tale.. look more carefully!

Regards
Colin

---

