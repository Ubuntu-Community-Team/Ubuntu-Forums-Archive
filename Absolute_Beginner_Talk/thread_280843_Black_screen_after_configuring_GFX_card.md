---
title: "Black screen after configuring GFX card"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by ChrisA on 2006-10-20
Hi

I'm a brand new user to Linux, just installed Ubuntu (had to boot from the LiveCD in "graphics safe mode"). After a sucessful installation, I downloaded all the software updates, then configured my graphics card by running [sudo dpkg-reconfigure xserver-xorg]. When I restarted, it got past the Ubuntu spash screen fine but when the screen just turned black and doesn't get any further.

I've tried rebooting again but i still get the black screen after the splash. :( 

AMD64 3200+
ATI X850XT 256 PCI-e

Any help appreciated.

---

### Post by Chaffar on 2006-10-20
Did you try to alt+F2 (or F3/F7) when you get the black screen?

If you get a login prompt, then the black screen is probably due to a misconfiguration of your video settings, and most probably because you installed the wrong drivers for your ATi card (which I think is not supported by the fglrx driver).

---

### Post by ChrisA on 2006-10-20
Alt+F2/F3/F7 does nothing.

I followed the guide here: [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

I didn't understand why it asked me to choose the fglrx driver? There was an ATI option there but I figured the guide would be correct.

When I press the monitor's on-screen display it appears, showing the correct resoloution.

---

### Post by ChrisA on 2006-10-20
Okay, weird...

I just restarted again and this time, no black screen! I entered my login and password, it began to load but then the monitor clicked off and reported "signal out of range".

What's going on?

---

