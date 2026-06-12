---
title: "trouble installing graphics driver"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Blandust on 2007-03-26
I am new to Ubuntu, I recently installed a new graphics card  I am unable to update the drivers in linux, Ive already installed the drivers on XP. I have a GeForce FX5200 256 agp.
 The problem is when I start Ubuntu I get a message telling me - Failed to start the x server. It is likely that it is not set up correctly, would you like to view x output to diagnose?
     After that im lost , Need some help thanks.

---

### Post by taurus on 2007-03-26
Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure xserver-xorg
```
Use **vesa** driver for your graphic card for now and if you are not sure about a question, just use the default.  When done, reboot with

```
shutdown -r now
```
Now, install envy and use it to install nVidia driver for your graphic card.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

