---
title: "OpenGL and GLX errors in wine"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-27
I installed wine and did the winecfg thing but in terminal, but when I type wine I get this error message
"Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems"
 The gui comes up but is choppy and sometimes unresponsive for a few minutes at a time. What do I need to correct this problem ? Thanks for the help.
This is on my Toshiba Satellite Pro - 768 Ram - Pent4 - 40  Gig HD - dual boot Feisty/XP

---

### Post by cogadh on 2007-07-28
You probably need to install the accelerated driver for your video card. Do you know what video chipset you have?

---

### Post by jerrynewt on 2007-07-28
My car is the nVidia Corporation NV17 [GeForce4 420 Go] .

---

### Post by cogadh on 2007-07-28
Then you should install the nvidia-glx driver. Follow this instruction [here]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") **to the letter** and you should have no problems.

There are three methods of installing the driver listed on that page, I recommend using method 1.

---

