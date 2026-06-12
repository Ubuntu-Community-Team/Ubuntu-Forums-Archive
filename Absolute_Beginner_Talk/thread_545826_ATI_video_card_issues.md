---
title: "ATI video card issues"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-08
I followed the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

To install my Radeon 9600 card.

Followed it step by step.

My sound stopped working (yet again).  But the strange thing is that when I first pulled up terminal and ran glxgears it was showing me 8000+ FPS... I opened up a web browser and decided to check it again... this time when I opened glxgears I got a FPS of 200.  I didn't do anything...

3D rendering is ON.  Does anyone know what might have happened?

---

### Post by Ek0nomik on 2007-09-08
What does "fglrxinfo" display?

---

### Post by ExSuSEusr on 2007-09-08
@Neo:~$ fglrxinfo

> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

Ok this is strange!!

> @Neo:~$ glxgears
26620 frames in 5.0 seconds = 5323.895 FPS
42590 frames in 5.0 seconds = 8517.956 FPS
42589 frames in 5.0 seconds = 8517.666 FPS
42575 frames in 5.0 seconds = 8514.809 FPS
42485 frames in 5.0 seconds = 8496.885 FPS

Looks good right?  Well I closed the terminal window... reopen it...  run glxgears again and now it shows:

> @Neo:~$ glxgears
1370 frames in 5.0 seconds = 273.872 FPS
1321 frames in 5.0 seconds = 264.197 FPS
1305 frames in 5.0 seconds = 260.997 FPS


I rebooted - opened terminal - ran glxgears and got 8500 FPS.  I close the terminal, reopen it right back and run glxgears again and then get 200FPS...  I didn't do anything at all this time.

---

### Post by Ek0nomik on 2007-09-08
Did you follow this portion of the website:  Method 1: Install the Driver the Ubuntu Way?  Or did you follow something else?

---

### Post by ExSuSEusr on 2007-09-08
I followed it the Ubuntu way.

3D rendering is ON as well.

I got Doom 3 up and running, but it's a bit choppy which is what prompted me to reboot and check the FPS and info.

---

