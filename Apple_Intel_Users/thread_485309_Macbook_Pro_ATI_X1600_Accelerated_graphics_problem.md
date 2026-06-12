---
title: "Macbook Pro ATI X1600 Accelerated graphics problem - slow graphics"
date: 2007-06-26
forum: Apple Intel Users
---

### Post by xelapond on 2007-06-26
I have one of the first gen macbook pros:

ATI Mobility Radeon x1600 128mb
Core Duo 2.0 Ghz

I installed the FGLRX driver for the ATI card.  It says i have installed the driver and it is enabled, but does not really accelerate the graphics much...

For example, it lags on the the matrixview screensaver, which to me looks really simple.

I am not positive i installed it correctly, so if there is a way to check that please let me know.

Also, if there is some little thing I may have missed..

Alex

---

### Post by ronocdh on 2007-06-26
> **xelapond said:**
> I have one of the first gen macbook pros:

ATI Mobility Radeon x1600 128mb
Core Duo 2.0 Ghz

I installed the FGLRX driver for the ATI card.  It says i have installed the driver and it is enabled, but does not really accelerate the graphics much...

For example, it lags on the the matrixview screensaver, which to me looks really simple.

I am not positive i installed it correctly, so if there is a way to check that please let me know.

Also, if there is some little thing I may have missed..

Alex
What was the method you used to install the driver? What output do you get from the command **fglrxinfo**?

---

### Post by xelapond on 2007-06-26
fglrxinfo gives me:


Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I don't remember what method I used to install it.

---

### Post by ronocdh on 2007-06-26
> **xelapond said:**
> fglrxinfo gives me:


Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I don't remember what method I used to install it.
OK, that means the driver is installed by isn't being used. First try running
```
sudo dpkg-reconfigure xserver-xorg
```
That should allow you to declare the ATI driver manually. If that doesn't solve your problems, you might want to remove the fglrx driver and re-add it by the following method:
```
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
That should work. You might need to run the dpkg-reconfigure command again, but I doubt it. Good luck, please post back.

---

### Post by xelapond on 2007-06-26
Thank you so much!  The first method worked, and now the graphics are actually bearable!

Thanks!

Alex

---

### Post by xelapond on 2007-06-27
OK, this is really weird..

I had the machine sitting, playing some music while i was working on my other one, when i turned around and noticed the screensaver acting laggy again.  I ran FGLRXinfo and got this again:

alex@AlexBook-Ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

alex@AlexBook-Ubuntu:~$ 

What should i try now?

---

### Post by ronocdh on 2007-06-27
> **xelapond said:**
> OK, this is really weird..

I had the machine sitting, playing some music while i was working on my other one, when i turned around and noticed the screensaver acting laggy again.  I ran FGLRXinfo and got this again:

alex@AlexBook-Ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

alex@AlexBook-Ubuntu:~$ 

What should i try now?
Odd indeed. I would try redeclaring the fglrx driver as you did before, then restarting the X by pressing ctrl+alt+delete. (You could do a full system reboot, if you want.) If that doesn't work, try removing the fglrx driver and then reinstalling with the method above. Hope this helps, please post back with results.

---

### Post by xelapond on 2007-07-06
OK, I reinstalled fglrx and it works fine now, been working for a week.

Thank you greatly for you time.

Alex

---

