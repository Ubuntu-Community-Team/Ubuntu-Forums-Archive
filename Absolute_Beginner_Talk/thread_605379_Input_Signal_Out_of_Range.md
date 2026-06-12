---
title: "Input Signal Out of Range"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-07
This problem did not appear with Feisty but has appeared after a fresh install of Gutsy on three separate machines.  The machines are running either Pentium or AMD chips on ASUS or Gigabyte motherboards.  Two machines have nvidia and one does not.

When the computer is powered on, the Ubuntu logo appears on screen. Then a white rectangle appears with the words "Input Signal Out of Range". This rectangle disappears as Ubuntu moves on with the loading. The rectangle may then reappear as the machine powers down.  

How can I get rid of this event?

---

### Post by ubnewbie2 on 2007-11-07
Could be a similar problem to mine, where my laptop screen would go blank.

Install startupmanager and set grub to use a sane resolution - I chose 1024x768 16 colours.

---

### Post by inversekinetix on 2007-11-07
It sounds like the default setting for resolution or refresh rate that your display driver is using is too high for your actual display.  There should be a config file somewhere that tells your driver the limits of your hardwares capabilities.  If not you can look at your hardware vendors website and find it yourself then make the necessary changes to your display settings.

Running a monitor/display at higher settings than it is made for can damage the hardware.

---

### Post by ubnewbie2 on 2007-11-07
> **inversekinetix said:**
> It sounds like the default setting for resolution or refresh rate that your display driver is using is too high for your actual display.  There should be a config file somewhere that tells your driver the limits of your hardwares capabilities.  If not you can look at your hardware vendors website and find it yourself then make the necessary changes to your display settings.

Running a monitor/display at higher settings than it is made for can damage the hardware.

If the problem was in X windows, I would agree, but it sounds like it's only during startup and shutdown, hence telling the kernel what video mode to use, might work. This I believe, is what startupmanager actually does.

---

### Post by expatCM on 2007-11-07
Startupmanager is a nice find .... fixed the problem on all three computers :)

Thanks for your help ...

---

### Post by Tony3286 on 2007-11-07
I'm having the same problem with Gutsy - just on startup and when shutting down.
Could you tell me what you changed in Startup Manager - was it just the resolution and are you now getting the splash screen? I've been trying for 3 months - first with Feisty now with Gutsy to correct this out of range problem. I've adjusted my resolution to 1024x768 - gone into Monitor/resolution and pressed TEST only to get a herringbone screen and test failed. Would appreciate any advice on what you did to correct the problem
Tony

---

### Post by expatCM on 2007-11-07
All I did was change the resolution to 1024 x 768 and the color depth to 16 bit.  These changes were on the first tab of the program (the identified settings before change were 640 x 480 and 8 bit).

---

### Post by Tony3286 on 2007-11-07
Wow! Thats exactly what I had 640x480 and 8bit - then changed to 1024x768 16bit.
But No cigar for me, still the same problem!
Well thanks for the reply, back to the posts for ,HOPEFULLY, more suggestions

---

### Post by ubnewbie2 on 2007-11-07
> **expatCM said:**
> Startupmanager is a nice find .... fixed the problem on all three computers :)

Thanks for your help ...


No probs - happy to return some of the great help I have, myself, received here.:)

For the developers, it seems there's a little tidying up to be done in this area....

---

