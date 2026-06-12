---
title: "How to be sure if Ubuntu can run on your Machine."
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by reynal_sf on 2007-07-04
Any help here?

[Product Specifications]

-HP Pavilion a418x
-Windows XP (32bits)
-Memory: 512 RAM
-Base processor: Intel Celeron 2.70 GHz:
                            400 MHz front side bus
                             Socket mPGA478

-Video Graphics: nVidia GeForce FX5500 256MB PCI
-Motherboard Description: MB manufacturer name: MSI MS-6577
                                           HP name: Gamila-GL6E

I can't run Ubuntu, it gives me this error... I have been reading problem just like this one, and never found a solution, anyone out there with knowledge on this problem?

[IMG]http://i82.photobucket.com/albums/j264/Airforce_sf/UbuntuError.jpg[/IMG]

---

### Post by Circus-Killer on 2007-07-04
are you trying to boot off the liveCD?

if so, you can try this: i doubt this will work for you, but you can give it a try. on booting the live cd, you get presented with a menu. press F6, which allows you to edit the kernel line. add "noapic irqpoll noirqdebug" to the line.

if successful, once ubuntu is installed, you will need to edit /boot/grub/menu.lst and add those same options to the kernel line. hope this helps.
laters.

---

### Post by reynal_sf on 2007-07-04
Thanks, I'll try this... if anything I'll let you know, peace.

---

### Post by gruffy-06 on 2007-07-04
A few hints:

1. Have you downloaded the correct version of Ubuntu for your architecture? Since you have an MS Windows operating system, your architecture is an x86 (sometimes called i386). Other architectures will not work.

2. Enter the BIOS config menu (normally by pressing F2 or Del, check your HP manual for info) and check the following: a) Any "memory hole" options are disabled; b) The install media you are booting from is at the top of the boot list.

3. If installing from a CD, check if you have burned it correctly. You may wish to burn your CDs at the lowest speed to reduce errors on your media. If that doesn't work, then either your CD drive does not work properly or your CD image is corrupt (you may need to download again).

Hope this helps...

---

### Post by reynal_sf on 2007-07-04
The CD works just fine, I installed Ubuntu on my brother's PC with this CD, and his PC Specifications is 

CPU: 2.0GHz
Memory: 256 RAM
Video: 64 (Shared Memory)

---

### Post by reynal_sf on 2007-07-04
By the way... I CAM boot to the Ubuntu menu, but when I click Start or Instal Ubuntu, that error comes out... :( (Just a reminder)

---

### Post by gruffy-06 on 2007-07-04
> **reynal_sf said:**
> The CD works just fine, I installed Ubuntu on my brother's PC with this CD, and his PC Specifications is 

CPU: 2.0GHz
Memory: 256 RAM
Video: 64 (Shared Memory)

Looks like a complicated situation. Ubuntu might not recognise some of your hardware properly or maybe it is an undiscovered fault. Not really much I can understand, though.

EDIT: Try a safe graphical boot.

---

### Post by waggygee on 2007-07-04
What version of Ubuntu is you Live CD?
This is a total shot in the dark... but if I were you I would try a different version of Ubuntu, if your trying 6.06 then give 7.04 a try or if your trying 7.04, give 6.06 a try. Can't promise it will help but maybe the different version is able to recognise your hardware properly (as this version seems is not able to do)

---

### Post by reynal_sf on 2007-07-04
I've tryed eveything.

---

### Post by reynal_sf on 2007-07-04
I have Ubuntu 7.04

---

### Post by meborc on 2007-07-04
have you tried alternative cd install? (when downloading iso from ubuntu website tick the "alternative" box) this will give you a non-gui install...

---

### Post by aquavitae on 2007-07-04
Hae you tried the alternate install cd?  It installs through the console (no X) so it might work.

---

### Post by reynal_sf on 2007-07-04
Yes I have tryed that too... and it instals it, but when it comes to boot, the same error comes out.

---

