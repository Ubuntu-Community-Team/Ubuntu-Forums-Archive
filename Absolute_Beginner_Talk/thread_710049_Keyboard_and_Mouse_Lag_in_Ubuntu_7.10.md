---
title: "Keyboard and Mouse Lag in Ubuntu 7.10"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by LagKills on 2008-02-28
Hi everyone,
I'm dual booting Unbuntu and Vista on my computer, Vista was first.

I Installed Ubuntu 7.10 onto my computer yesterday and ever since I rebooted the first time after installation my mouse and keyboard have had a ridiculous amount of lag. The mouse moves very slow across the screen, and when I type I have to type really slow for it to pick up the keystrokes. Its like the frame rate has dropped. All the animations and videos on the desktop and internet run perfect without any hookups. I've tried installing new video drivers but every time I restart the lag is still there and the resolution is at 640*480. I've installed all the updates and unrestricted the video card.

When i go back to Vista everything runs normally. I partitioned 10GB for Ubuntu, using Vista not a third party software. When I was on Ubuntu during installation with the Live CD, it ran perfectly. But once I restarted my computer and loaded up Ubuntu again the keyboard and mouse were slow. I'm brand new to Linux, I know how to load up the terminal but I have never used it before. Please help.

I built my computer myself here are the specs..

MOTHERBOARD: ASUS P5W DG Deluxe
CPU: Intel(R) Core(TM)2 CPU 6700 @ 2.66Hz 2.67 Ghz
RAM: 2.00 GB
GPU: NVIDIA GeForce 8800 GTS 640MB

MOUSE: Logitech Mx518 1600 DPI
KEYBOARD: Logitech G15
MONITOR: Samsung 23'' LCD TV (using DVI to HDMI cable)

---

### Post by talsemgeest on 2008-02-28
I think your mouse might be sending too much info for ubuntu to keep up with. You can try lowering the senitivity in system>preferences>mouse.

But as for the keyboard, I have no idea...

Hope this helps :)

---

### Post by LagKills on 2008-02-29
I messed with the mouse settings but that didn't help..

I've installed a few different video drivers but none of them have helped..

Has anybody else had this problem?

---

### Post by talsemgeest on 2008-02-29
I'm pretty sure it isn't the graphics drivers. BTW is it wired or wireless?

---

### Post by LagKills on 2008-02-29
The mouse and keyboard are both wired. (USB)

---

### Post by forrestcupp on 2008-02-29
It's possible it's the video drivers.  I think you don't understand something.  You don't want to 'unrestrict' your video card.  That's not what that means.  The Restricted Drivers Manager installs the 'restricted drivers' for you, which is something you probably want.  Restricted drivers are the proprietary drivers that nvidia puts out.  It just means the drivers aren't open source.

So if you 'unrestricted' your video card by unchecking that box in the Restricted Drivers Manager, you did the wrong thing.  Just open it back up and check the box for nvidia drivers.  It will install them, and hopefully that will help.

If not, open the Restricted Drivers Manager back up and uninstall the drivers, then try using [Envy](http://albertomilone.com/nvidia_scripts1.html) to install even newer drivers than what are in Ubuntu's repositories.  I'm not totally sure that the drivers in the repositories support the 8800 very well, so you might need the newer ones.

If you get through all that and still have problems, we know it's probably not your video drivers.

---

### Post by LagKills on 2008-03-19
I solved the problem!

I just pulled the mouse and keyboard into different USB ports. I had them plugged into extra USB ports that were below my video card, using a PCI slot. I now have them plugged into ports that are built onto the motherboard.

---

### Post by talsemgeest on 2008-03-23
Ah, glad you have it fixed!

---

