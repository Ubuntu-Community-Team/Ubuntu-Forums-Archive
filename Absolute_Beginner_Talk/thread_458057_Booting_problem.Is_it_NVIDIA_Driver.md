---
title: "Booting problem.Is it NVIDIA Driver?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ichimeno on 2007-05-29
Hi i just installed Ubuntu from the alternate Cd and all worked fine. I rebooted my pc and it had the ubuntu logo and the orange bar goin. After it was done loading, the screen turned all wierd with lines of orange. it did not show the user screen. Is it because of the graphic card i have? I have a NVIDIA Geforce 6800. Is there a way i can fix the prob and boot up to my account? thnx in advance:D

---

### Post by lazyart on 2007-05-29
Boot up and when you see the text GRUB screen, hit ESC and select recovery mode.  

Once in, type```
dpkg-reconfigure xserver-xorg
```You'll see a familiar screen to set up your video hardware.  Accept the defaults, but be sure you pick NV as your video card.  When done with the 2 dozen or so pages of setup, hit control-alt-delete and reboot.

This should let you log in.  You'll then want to enable the restricted driver from System>Adminstration>Restricted Driver Manager

---

### Post by ichimeno on 2007-05-29
Ok Thank you Lazyart i will try this right now


EDIT: I tryed but it still didnt work. I chose the NV for video card and press enter to all the pages. Did i do anything wrong?

---

