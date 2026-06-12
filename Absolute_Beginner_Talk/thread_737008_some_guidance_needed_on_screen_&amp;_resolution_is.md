---
title: "some guidance needed on screen &amp; resolution issue"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by PeterVonSaints on 2008-03-27
Hi everyone,

I decided to install ubuntu 7.10 on my laptop - sony vaio VGN-T2XP/S - which also runs XP SP2. Booting from ubuntu Live CD, everything goes fine until it displays a messy GUI on the screen. Instead of the expected 1280x768 I get 640x480, the GUI displays on the upper left half of the screen, the right half of the screen is black and at the bottom a white rectangle. 

On screens and graphics:
Screen - the only resolutions I find are 640x480/400/350, when I try to choose manually LCD model  I don't find the proper screen resolution, the nearest one is 1024x768 and If I choose widescreen it will report that the application crashed. 
Graphics Card - it displays "Intel Experimental modesetting driver for..." and I am not able to find my  Intel 82852/55 card

Thought that it might be different with Xubuntu, so downloaded livecd and the result was exactly the same. 
In the initial menu if chosen 1280x768 makes no difference. Is this an issue with this specific graphics card? Is it Ubuntu specific? I saw some posts with similar problems but honestly don't understand so I'd really appreciate some help/guidance

Thank you

---

### Post by Ub1476 on 2008-03-27
You need to install (you can press <Alt>+Mouse to drag windows around), then download the intel driver. I believe it's called i810 or something. Someone else can probably shed some more light on this..

---

### Post by phrawzty on 2008-03-27
> **PeterVonSaints said:**
> 
In the initial menu if chosen 1280x768 makes no difference. Is this an issue with this specific graphics card? Is it Ubuntu specific? I saw some posts with similar problems but honestly don't understand so I'd really appreciate some help/guidance

Hello,

This is almost surely an issue with the specific graphics card (an integrated Intel, if memory serves).  The only solutions i've seen for this issue involve changing your Xorg.conf (the configuration for for Xwindows - the GUI) - which, if you're using the LiveCD - will not be permanent.

As well, some people have reported success with the "xserver-xorg-video-intel" package :
```

$ apt-cache show xserver-xorg-video-intel
   ...
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family
 of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
 and i965 series chips.

```

You could try installing that when in a LiveCD session and seeing if it helps with your resolution problems.

---

### Post by sillyxone on 2008-03-27
I remember when I first install Feisty, I had to use 915resolution tool to set the resolution correctly. However, since Gutsy (fresh install), the graphic works very well with either i810 or intel driver.

---

### Post by PeterVonSaints on 2008-03-27
POS,
As recommended I did the apt install of the driver - it told me I already had the latest release - the problem persisted. 
Before trying anything more tricky like configuring xorg.conf I decided to check the BIOs and eventually saw this option ** LCD screen Expansion**, changed it from **No** to **Yes**. Just after that, there's a slight distortion on the initial menus (same on windows) but everything looks fine, correct resolution 1280x768, I'll now proceed with the install.

Big thank you for your answers and suggestions

---

### Post by phrawzty on 2008-03-27
> **PeterVonSaints said:**
>  but everything looks fine, correct resolution 1280x768, I'll now proceed with the install.

Big thank you for your answers and suggestions

Great - i'm happy to hear it.  If you like, you can press the "thank you" icon beside the name(s) of the person(s) who helped.  As well, it's always a good policy to insert "[SOLVED]" into the title of the thread (just edit the thread), so that people who are searching the archives in the future can spot the solutions more quickly.

Cheers !

---

