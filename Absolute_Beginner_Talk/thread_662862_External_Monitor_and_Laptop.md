---
title: "External Monitor and Laptop"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by dgoodma on 2008-01-09
I have an external monitor attached to my laptop. All works well when I boot that way. If I try to plug in the monitor while the laptop is already on, it does not work. The Function Keys that work under Windows seem to have no effect.

Normal to have to reboot, or should it just not work by plugging in?

---

### Post by annda on 2008-01-09
you could just try restarting the X server, it's much faster and should work.

CTRL+ALT+BACKSPACE

after restart you will see the standard login screen.

---

### Post by Pevichaey5 on 2008-01-09
the function keys on laptops mostly work with windows, however my current laptop just about all of them work, i just need to assign a couple

if you connect the other monitor while linux is running, can you go to System>>Administation>>Screens and Graphics and manually activate the screen?

---

### Post by someoneouthere on 2008-01-09
irrelevant question.....what is/means " de xero"? :lolflag:

---

### Post by lgambett on 2008-01-09
If you have an nVidia card the program nvidia-settings will manage that issue for you.

---

### Post by dgoodma on 2008-01-09
I have nvidia, I installed nvidia-settings. Does it only launch from a Terminal Session? I launched it there, did not see that it does anything.

My videos is working, and all of the desktop effects stuff after I installed all of that.

What I get when I launch nvidia-settings  ... more to the story I presume, as seems to the be case a lot... :)  but, will get there I am sure.

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':1.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':1.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':1.0'.

---

