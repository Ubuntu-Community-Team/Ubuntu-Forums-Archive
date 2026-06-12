---
title: "[SOLVED] install video driver at boot?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-05
I'm finding it impossible to install a PNY GeForce 6600GT video card.  I have several posts detailing the aggravating steps I have taken, so I won't repeat those here.  

I seem to remember reading somewhere that you could push a function key of some sort at boot and install a video driver right then at boot time.  Given everything else I have done this is about all I can think of that is left to try.  So:

(1) What do I have to have on what kind of disk to use at boot to install the nvidia driver of some sort for my card (heck, what driver???)

(2) Just exactly how do I go about that on the LiveCD?  I want to do a complete from scratch install with this card, but as soon as the LiveCD goes GUI (the X GUI - default Gnome) I can't read my screen anymore.  Tried the alternate CD - got to 97% done and hung.

Help!!!!!!  :confused:

---

### Post by talsemgeest on 2008-04-05
Ok first boot into recovery mode.

When you get to the command line type this: 
```
sudo apt-get update
sudo apt-get install nvidia-glx-new
```
This should install your driver, provided the nvidia-glx-new driver is the one you need.

Hope this helps :)

---

