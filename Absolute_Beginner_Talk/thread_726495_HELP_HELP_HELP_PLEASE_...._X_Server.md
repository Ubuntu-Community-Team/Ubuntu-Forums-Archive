---
title: "HELP HELP HELP PLEASE .... X Server?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by HackaEcho on 2008-03-16
X Server Doesnt load and questions may to reconsile... When i Reconsile it repeats the Mesage at the bottom of my computer specifications as No Screen. 

And therefore i can only Tab and go to Okay and pressing Enter.

i Dont Know What to do how to fix this.. Anyone know?

IM using Wibi on 7.04 and Dual Booting. Linux Ubuntu. So Please Give Us A shout with Guru ADVICE :)

---

### Post by bsharp on 2008-03-16
type this in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by HackaEcho on 2008-03-16
> **bsharp said:**
> type this in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

U ROCK! <3

---

### Post by bsharp on 2008-03-16
Glad i could help ;)

---

### Post by HackaEcho on 2008-03-16
> **bsharp said:**
> Glad i could help ;)

One Thing.... New To This... Been Drinking Tea for The last Few minutes. How do i "Access" Terminal? If i said that correctly. Because when i Load its basically

Black Screen White writting...

And/or.. I See 

Errors:
No Screen ...

So Whts This terminal.... Sorry for the Newbieness...

---

### Post by bsharp on 2008-03-16
Push Ctrl+Alt F1 to switch from the failed X to a terminal (now that I think about it, I believe the correct term is "console") and enter the reconfigure command there.

---

### Post by HackaEcho on 2008-03-16
> **bsharp said:**
> Push Ctrl+Alt F1 to switch from the failed X to a terminal (now that I think about it, I believe the correct term is "console") and enter the reconfigure command there.

One Again U ROCKz

u are OMFG,WTF,PWNED,IN,THE,FACE,SHEMO!! :)

<3 lol

---

### Post by HackaEcho on 2008-03-16
> **bsharp said:**
> Push Ctrl+Alt F1 to switch from the failed X to a terminal (now that I think about it, I believe the correct term is "console") and enter the reconfigure command there.

Right More problems... after i enter this "console" I can select teh screen resoloutions which is brlliant :) Im Furhter than what i was, but it doesnt seem to be saving the resouloutions or something... because it keeps loading to the same screen complainging about the X server? So Im Completly Confused.. Is there a way .. do I Have to save the resoulutions; If so How? if ur still there BSharp??

---

### Post by bsharp on 2008-03-16
it sounds like you need to install a driver for you video card, what kind are you using?

---

### Post by jken146 on 2008-03-16
Try ```
sudo dpkg-reconfigure xserver-xorg
``` without the -phigh option.  It might not be just a resolution problem.  Do your best with the questions; if in doubt pick the defaults.

---

### Post by HackaEcho on 2008-03-16
> **bsharp said:**
> it sounds like you need to install a driver for you video card, what kind are you using?


This is what im using:
Hp (Compact) Laptop: Presario 6500 .. If that helps

Video adapter
 Intel® Graphics Media Accelerator X3100
 
Video RAM
 Up to 384 MB total available graphics memory 

Display size
 15.4” WXGA High Definition BrightView Widescreen
 
Display resolution
 1280 x 800
 
Thats all i know? >< Sorry... Can u guys still help? lol Sorry For all this hassle...

---

