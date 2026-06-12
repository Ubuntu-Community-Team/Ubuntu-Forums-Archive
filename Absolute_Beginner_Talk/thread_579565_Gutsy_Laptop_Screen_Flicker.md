---
title: "Gutsy Laptop Screen Flicker"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by phr0ze on 2007-10-18
With fiesty, I didn't get the flicker but the desktop didn't fill the screen. With Gutsy, the resolution is right out of the box, but I get a very rapid flicker, especially in the darker background. It seemed like a refresh issue, so I changed it from 30 to 60hz in the resolution panel. I also tried lowering the resolution too.

I don't have any flicker in windows. Its a laptop so finding the proper frequencies has been difficult.

Fujitsu p5020 
xorg.conf is using Intel Corp 82852/855GM integrated graphics device.

---

### Post by Frenezo on 2007-10-18
Fujitsu Lifebook 8010D integrated intel 855, same problem here :(

Seems like gutsy uses another way to get the real resolution to e.g 1400x1050.

---

### Post by ibanez88 on 2007-10-22
Which graphics card driver are you using?  I had the same problem until I switched my driver to i810.  The autodetected selection which gave me the flicker was "Intel".

---

### Post by Frenezo on 2007-10-22
intel 855

---

### Post by xdevnull on 2007-10-22
Here's how I fixed mine:

Go to system:administration:screen & graphics

click on graphics card tab: select the i810 driver (intel integrated graphics).

Click OK.  OK again - says I have to logout to take effect.

Do that - Woah - everything is wonky - its 1024/768.  Mouse won't show up.  Wait - it's there, but I can't see it.  I manage to get the screen & graphics prefs up again.  Ah - there is a widescreen box to click. 

Do that - logout and in - flicker is gone, resolution is right!

---

### Post by phr0ze on 2007-10-22
I'll try this... Did it solve anyone else?

---

### Post by luckylucky on 2007-10-22
I tried the above but it didn't work for me.  Anyone able to help please?

---

### Post by Inxsible on 2007-10-24
I use Nvidia 7600 and I too have the flickering screen problem. I use 64bit Gutsy though. Which ones are you using?

I found a couple of thread in the 64bit forum

[http://ubuntuforums.org/showthread.php?p=3624199](http://ubuntuforums.org/showthread.php?p=3624199)

[http://ubuntuforums.org/showthread.php?t=398821&page=11](http://ubuntuforums.org/showthread.php?t=398821&page=11)

---

### Post by DarthGroznii on 2007-10-25
> **Inxsible said:**
> I use Nvidia 7600 and I too have the flickering screen problem. I use 64bit Gutsy though. Which ones are you using?

I found a couple of thread in the 64bit forum

[http://ubuntuforums.org/showthread.php?p=3624199](http://ubuntuforums.org/showthread.php?p=3624199)

[http://ubuntuforums.org/showthread.php?t=398821&page=11](http://ubuntuforums.org/showthread.php?t=398821&page=11)


Experiencing the same issue here with a Lenovo 3000 N200, with an Nvidia graphics card.

It's not consistent - it only kicks in after use for about 10 minutes.

---

### Post by ryanchew on 2007-10-25
I'm using an Asus A8Js laptop with a Geforce Go 7700 gfx card.
I was having the same screen flicker problem and decided to mess around with nvidia-settings.

Try setting the following options in nvidia-settings:
```

X Screen 0 -> X Server XVideo Settings -> Sync to VBlank (Check)
X Screen 0 -> OpenGL Settings -> Sync to VBlank (Check)
X Screen 0 -> OpenGL Settings -> Allow Flipping (Check)

```

You will have to apply these settings to other flickering screens as well (if you have any) but I was only able to test it on one screen.
Like some games on some screens, it seems to be a problem with VSync, so compiz users will probably experience this as it's OpenGL accelerated.
I'm not sure how to set the VSync/VBlank options for ATI and Intel cards but if someone could point out how, it will probably fix the problem as well.

Let me know if this helps cos it seems to have worked for me. :)

---

### Post by ph1 on 2008-01-23
I would also recommend checking out [this thread]("http://ubuntuforums.org/showthread.php?t=398821&page=12"), which seems to have worked for many people, and seems to be a quick and easy fix that you could try first.  I just tried it, and it's too soon to tell, but I think it may have worked for me.

EDIT:  Nope, didn't work.

---

### Post by ph1 on 2008-01-24
OK, I think I finally found what was causing the flashing problem for me.  It's listed in [this thread]("http://ubuntuforums.org/showthread.php?t=398821&highlight=screen+flashes+black&page=13").  The screen is flashing black when the gpu switches its clock speed to save power.   Emerald, Compiz, etc. cause it to flick up into 3D mode (flash) and then later, when you're just browsing or something, it flicks back (flash again).  

If this is your problem, you can watch this happen.  Type in a terminal "nvidia-settings -q GPUCurrentClockFreqs", note the clock speed, and then as soon as you see a flash enter it again--the clock speeds will be different.  I kept entering it until another flash, and it failed to change until the second flash.

To fix this, you can lock your graphics card in a single mode--2D if you want to save power, 3D if you want your effects.  You can also use Coolbits (if your driver supports it) to open the overclocking options and, without necessarily overclocking, manually set the clock speed.

Also note that in 3D mode you'll get a lot more heat.  You may want to consider a temperature monitor/fan control to help with this problem.

This is stupid that fixing this problem creates other problems, but I'd rather have my fans run longer and drain my battery than to have to deal with that maddening flicker or burning up my laptop.

---

### Post by johnnyzazza on 2008-01-25
This may resolve the issue for you:

Add the line:

> options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"

to /etc/modprobe.d/nvidia

More info at: [http://www.nvnews.net/vbulletin/showthread.php?t=96673]("http://www.nvnews.net/vbulletin/showthread.php?t=96673")

---

### Post by ph1 on 2008-01-26
Thanks, johnnyzazza, that did fix it for me.  However, I'm getting some excessive heat from the GPU.  I've tried underclocking using coolbits, but the settings won't stick.  Might you (or anyone else) know how to fix this?  (I'm using a GeForce Go 7950 which is way too much power for what I do in ubuntu , and I'm looking to minimize heat and power settings.)

---

