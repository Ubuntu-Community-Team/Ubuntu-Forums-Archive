---
title: "Any luck installing Ubuntu on a Powerbook G3 Wallstreet?"
date: 2004-12-02
forum: Apple PPC Users
---

### Post by monkeyshaman on 2004-12-02
I just recently aquired a 1998 G3 (Wallstreet) and I put Yellowdog 3.0 on it, but would like to try Ubuntu instead.  I see where someone installed it on a Beige Mac.  Was wondering if that same method would work for me?   :???: 


Arnold

---

### Post by spence on 2004-12-06
[QUOTE=monkeyshaman]I just recently aquired a 1998 G3 (Wallstreet) and I put Yellowdog 3.0 on it, but would like to try Ubuntu instead.  I see where someone installed it on a Beige Mac.  Was wondering if that same method would work for me?   :???: 


Arnold[/QUOTE]


I'm going to try it today so I will let you know

Spence

---

### Post by monkeyshaman on 2004-12-06
Well, I unfirtunately gave up on Ubuntu for now on my laptop and went back to Yellowdog.  It's just a little too "flaky" on the Old World laptops.  I'll continue to use Ubuntu on my PC and will try it again should I get a "New World" laptop.

Arnold

---

### Post by tlunde on 2005-01-25
Works fine for me.  1998 Wallstreet Series 1, 250mhz.  Installed to an external SCSI drive (just didn't want to mess up my OS X install on the internal drive until I was sure it would be OK).

One note:  If you find that you have a vertical line of fuzz running down the left
side of your screen after X starts, try adding:

video=atyfb:vmode:14,cmode:8,mclk:71 to your boot parameters in BootX

---

### Post by macke on 2005-02-08
Hi!

I need some help too, have yellowdog 3.0.1 installed but would like to try ubuntu.
Can I install ubuntu using bootx, If so how do I do that?

---

### Post by king_arthur on 2005-02-10
ubuntu_ppc on Apple powerbook G3 wallstreet working fine here :) 
 
 suggest you all have a look [here]("https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs") for some help
 
 I found the trick to copy the new kernel into the hfs partition useful..
 
 bear in mind that you have to run the installer twice: one for base system and a second time for installing a complete desktop.
 
 
 I also reccomend using icewm instead of standard gnome desktop as the memory requirements are much lower and you can run at decent performance even with only 64 Mbyte RAM
 That is BTW what I am doing right now...

---

