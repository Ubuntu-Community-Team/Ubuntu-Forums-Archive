---
title: "Webcam"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by swey on 2007-04-01
My webcam is showing as "USB camera" in device manager but I can't seem to access it. I've tried installing Camorama but it won't start - I get this error: "could not connect to video device dev/video0"

It didn't need specific drivers installing in Windows - does it need some now? Found nothing in the repository on this.

Ubuntu 6.10
ASUS webcam (came with graphics card)

---

### Post by johnny4north on 2007-04-01
i would try "camstream"  install from Synaptic package manager{panel>system>administation>synaptic package manager.  click All, then search "web cam" click box next to "camstream"  click Apply  your done..  thanks Ubuntu.

---

### Post by insane_alien on 2007-04-01
theres a kernel module you need to install for webcams. can't remember how you do it though, have a search through the community docs and run a search on the forum

---

### Post by EdThaSlayer on 2007-04-01
I have a creative webcam and I got it working by installing the "spca5xx-source" driver. Maybe that will work for you since it supports many different webcams. All you have to do is search for "Webcam" in synaptic package manager and then install "spca5xx-source" or a similar driver, you also might want to install "qc-usb-source" and "pwc-source" in case so you are sure your webcam will work.

---

### Post by nichipet on 2007-08-06
I don't know if anyone is still watching this thread, but I have camorama and camstream installed and my administrator account can use either program with the webcam, but my regular user account cannot. When the regular user tries to open camorama I get the "could not connect to video device /dev/video0" error.

I have a built-in Syntek webcam on an Asus Z84FM with Ubuntu Studio 7.04. In the original installation to get the webcam to work at all, I followed the directions from [http://www.sonic-world.com/blog/?p=51](http://www.sonic-world.com/blog/?p=51)

A second problem is the image in camorama or camstream is upside-down. I'm guessing that's either hardware or driver related.

---

