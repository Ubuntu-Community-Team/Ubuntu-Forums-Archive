---
title: "Screen Resolution Options"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by bob along on 2007-08-10
Everything is way too big on the screen so I tried to change screen resolution but found that I only have the choice of 640 x 480 but it should be 1024 x 768 (i think)..

---

### Post by SOULRiDER on 2007-08-10
Here you go:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Its a common problem, finding the solution wasnt hard, just try to doa  bit more searching next time ;)

---

### Post by Quinn5219 on 2007-08-11
> **SOULRiDER said:**
> Here you go:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Its a common problem, finding the solution wasnt hard, just try to doa  bit more searching next time ;)

How about 6 months of searching??  This one little glitch prevents me from using Ubuntu and my mail 
program will not work with the screen resolution so big.   I will keep looking for a solution, I am sure I will find it, but I have a sneaking suspicion that Windows is what will correct the problem.

---

### Post by codbla on 2007-08-17
1. open your favorite terminal program

2. make it a super user (sudo su)

3. issue the command (dpkg-reconfigure xserver-xorg)

4. change the X server driver (example vesa in the options given)

5. Follows those steps, until you will be given a resolution (choose only those your driver and monitor can support by default 1024x768, 800x600, 600x480)

6. You can test it, log out then log in again.

7. Adjust now your desired resolution.

I try it in the Windows running VMWare where Ubuntu is the guest OS, and using the HP Proliant ML110 server (where X server driver is mga)

you can visit my blogsite @ [http://codbla.blogspot.com:KS](http://codbla.blogspot.com:KS)

---

### Post by alienexplorers on 2007-08-17
Sometimes adding a modeline will force the new resolution.
> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 120.0
    ModeLine       "1280x1024_65.00" 119.4 1280 1368 1504 1728 1024 1025 1028 1063 -hsync +vsync
    Option         "DPMS"
EndSection
Works sometimes, but not everytime.

---

### Post by bob along on 2007-08-18
I used the link and added the vertical and horizontal refresh rates and it worked. I now have all the resolutions showing.

---

### Post by brett611 on 2008-03-18
Try this link.  The instrux look very straightforward and make sense conceptually

[http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html](http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html)

---

