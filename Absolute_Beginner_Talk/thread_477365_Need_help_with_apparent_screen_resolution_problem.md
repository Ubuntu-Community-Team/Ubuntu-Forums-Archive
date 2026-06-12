---
title: "Need help with apparent screen resolution problem"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by eulercircles on 2007-06-18
Hello, I am new to Linux and Ubuntu. I just installed Ubuntu on my laptop and I am having a hard time figuring something out. When I go into preferences to change the screen resolution, I get only two options - 640x480 and 800x600. I have it set to 800x600, but it is not really the resolution of my LCD panel - instead I get only an 800x600 screen in the center of my panel. In other words, it is not using my whole screen. If I set it to 640x480, the resolution doesn't really change, I only get a smaller box in the center of my screen. I think my resolution should be able to go up to 1280x1024.

I have a Sony Vaio laptop (PCG-FRV37) with an ATI Radeon IGP 340/345M graphics card. I can't find any drivers for it on either the Sony or the ATI websites.

I downloaded libdrm-2.3.0, but I can't get it to make. I can configure, but I get the following error when I try to make it:

[FONT="Courier New"]make: *** No targets specified and no makefile found. Stop.[/FONT]

Also, when I try to turn desktop effects on, I get only a blank white screen with a mouse pointer. If I go into Beryl Manager, I also get the same white screen.

Does anyone have any suggestions for me? Point me in the right direction.

Any help will be much appreciated. Thanks

---

### Post by qamelian on 2007-06-18
It looks like ATI no longer supports this chipset in the current drivers. You may be able to get it working with one of the older drivers at: [http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html](http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html)
Be sure to check the release notes to see if any of these support your card. There is no guarantee that any of them do especially since this is a laptop and laptop vendors are notorious for doing their own customizations to graphics chipsets.

---

### Post by eulercircles on 2007-06-18
OK. Thanks, qamelian. It won't work - those drivers do not support my card. I double-checked the Sony site, and they only have drivers for Windows XP and Vista. I will look up the specs on my desktop PC and perhaps do a dual install on that one. Once again, thanks!

---

### Post by Sand Lee on 2007-06-18
just run ```
sudo dpkg-reconfigure xserver-xorg
```, it'll take you through a setup and you'll be able to change you resolution to a higher one. I'm afraid I can't help you with the graphics driver though...

---

### Post by eulercircles on 2007-06-19
Hey Sand, Thanks a lot. That did the trick. Thanks to both of you. Now, if I can only get Anjuta working...

---

