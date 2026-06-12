---
title: "Blender Crashes X ?"
date: 2007-06-06
forum: Art &amp; Design
---

### Post by rcmullins on 2007-06-06
Not sure where to post this, but I am guessing this is a x-windows problem with gnome.

I have installed the graphics program Blender. Whenever I hit the F12 button (render), the render goes through its normal processes. However, when I grab the window and try to move it around the entire ubuntu freezes up. ctrl+alt+backspace doesnt work either. The entire system is completely un-responsive.

I have tried un-installing Blender 2.4.3, I have tried installing Blender 2.4.4 but this does not seem to be a Blender problem, but rather a problem with the x-windows system or gnome.

Any suggestions?

thanks.

---

### Post by Offoffoff on 2007-11-05
Your problem is not problem, man. I can not even start Blender. I am thinking it is due my Compiz-Fusion, but I do not like to switch off effects.

---

### Post by jespdj on 2007-11-09
Blender 2.44, which is the version currently in the Ubuntu repository, unfortunately has some bugs. Get [Blender 2.45](http://www.blender.org/download/get-blender/), which fixes a number of those bugs.

Unfortunately 2.45 is not in the Ubuntu repositories, but there's a *.deb file here: [http://www.getdeb.net/app.php?name=Blender](http://www.getdeb.net/app.php?name=Blender)

---

### Post by Catalyst2Death on 2007-12-18
I'm using blender 2.45 using python 2.5 and I have a similar situation.  My crashes seem to be much more random, and occur mainly when I try to render a scene. The  entire X server restarts as though I hit Ctrl Alt Del, but there are times when I crashes, I have to hit Ctrl Alt Del.  I've even had crashes that seize the whole system causing a hard reboot.  Needless to say, the crashes are frequent and it makes it difficult to be productive.

---

### Post by m1xram on 2007-12-20
OK, I got it, don't run blender. I was running 2.4.3 and the crashs were random always requiring a reboot with power button on laptop, a Dell 1420. I see there's no need to install 2.4.4 or 2.4.5 either.

So.. tell me about other 3D software you use.

As a side note, I'm a little bit bummed that it trashes X and / or Gnome. I was really hoping the window couldn't take out the window manager.

---

### Post by m1xram on 2007-12-20
I found a bug they're working on for an interaction with the i810 video driver. See [Bugzilla Bug 12164 at FreeDesktop.org]("http://bugs.freedesktop.org/show_bug.cgi?id=12164") if you use this driver. One of the last things mentioned is a problem with the Intel 945gm which sounds similar.

---

### Post by Catalyst2Death on 2007-12-22
unfortunately I am not running those drivers on my desktop (I'm going to work on my laptop now that I'm home for christmas)  so I'll be better able to report on bugs because my laptop and desktop share completely different hardware....

---

### Post by gravometric on 2008-03-13
I'm using the:
 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller 

When I first installed Ubuntu Studio, Blender worked with Compiz running (Firefox open, Gimp open, Inkscape open, Recording audio on different desktops of the cube).  I installed Jahshaka, and it ran with Compiz running.  I turned effects off because the brush was lagging behind my mouse in the Gimp, and now when I start Jahshaka *or*  Blender (full screen or windowed) my Xwindows restarts (as though Ctrl-Alt-Bksp) bringing me back to a login prompt.  I've tried to send an error message to a log file by starting from the command prompt with "&2> errorlog.txt", but that just gave me a blank file.  The only major work I recall doing with the system between "working" and "not" was to fix the sound card (install Alsa 1.0.16) and the get the Synaptics touchpad.to work (by adding a line in xorg.conf)

I'm using Ubuntu Studio (Gutsy Gibbon) with Blender 2.45 and Jahshaka 2.0.  Neither of them work with Compiz turned on or off.  

-9r/\\/|7y

---

