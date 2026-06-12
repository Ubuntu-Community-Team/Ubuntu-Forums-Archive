---
title: "Gutsy on Dell 1521 - 1280 x 800"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by will_ship on 2007-10-19
~ Hi

I am 18, brand new to Ubuntu and would like some help.

I have just installed Gutsy Ubuntu, dual booting with Windows Vista on a:

Dell Inspiron 1521 Laptop

Processor: AMD Turion 64 X2 Mobile Technology TL-50
RAM: 2 GB
Sound: SigmaTel HD Audio CODEC
Video Card: ATI Radeon X1270

On Windows VIsta my screen resolution is 1280 x 800 but on Ubuntu the highest it will go to is 1024 x 768. Everything works fine in Ubuntu on 1024 x 768 but I would like 1280 x 800.I don't know if i need to download a driver or what. I don't know how to download a driver! 

Thanks ALOT.

---

### Post by akkad on 2007-10-19
try this :
- system >>> adminstration >>> Restricted Drivers Manager
- check the enabled option near ur video card.
- u will be asked to download some new packages, proceed with dialog,
- when finish restart ur system, after the restart ur screen resolution will be 1280x800 by default.

---

### Post by will_ship on 2007-10-19
**This is my Restricted Drivers Screen:**

-----------------------------------------------------------------
______________Restricted Drivers__________X_|
...

v Driver
----ATI Accelerated Graphics Driver------O------Not in use

----------------------------------------------------------------

**When I check the Box a popup says:**


-----------------------------------------------------------------
__________________________________________X_|
...ENABLE THE DRIVER?

ATI accelerated graphics driver

This driver is required to fully utilise the 3D potential of ATI graphics cards, as well as provide 2D acceleration of newer cards.


-----------------------------------------|ENABLE DRIVER|-----


**When I click ENABLE DRIVER a Popup says:**


-----------------------------------------------------------------
__________________________________________X_|
The software source for the package

   xorg-driver-fglrx

 is not enabled.

----------------------------------------------|CLOSE|---------

[B]It then goes back to the Restricted Driver window unchecked and still "Not in use"

Is there a way to enable this?[/B]

BTY - Thanks for responding.

---

### Post by andrewsomething on 2007-10-19
You need to go to System >> Administration >> Software Sources 

There you can enable more software sources by checking off the boxes. Enable them all, and then repeate what you did above. That should get you running...

---

### Post by will_ship on 2007-10-19
You are awesome I am now using Ubuntu on 1280 x 800 perfectly. Thank you so much

---

### Post by liquidfunk on 2007-12-25
Which version are you using? 

 32bit/ 64bit?

 LiveCD or Install disc?

 I can't get it to go past a Xserver failure

---

