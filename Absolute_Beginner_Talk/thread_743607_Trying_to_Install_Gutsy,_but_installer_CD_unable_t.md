---
title: "Trying to Install Gutsy, but installer CD unable to detect graphics card/screen"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-04-02
I have a Dell Desktop Dimension 2350 with a Dell Monitor E772c. Now I have XP on the computer, and want to add Gutsy as a dual boot. I downloaded the Gutsy installer CD, but when I try to boot with it, it cannot reach to the desktop screen. It gives the Ubuntu insignia with the orange progress light going back and forth across the screen, but after that it can't get to the desktop screen. I tried booting up in the safety mode, and it tries but it ultimately gives the following message:

> Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself.

When I then opt to go into "configure" mode, it shows that it has correctly identified the monitor as Dell E772c. It assigned resolution as 640 x 480 @ 86 hz. And the graphics card it identified as Intel 845. Which, when I look at the other options it offers, the choice of 845 looks to be the closest. In XP device manager, the graphics is listed as Display Adapter: Intel (R) 82845G/GL/GE/PE/GV Graphics Controller. And the choice it selected is actually 845G. Which seems pretty close.

It also chose the driver as "Vesa - Generic Vesa-compliant video cards". I tried changing it to "VGA" but that didn't make any difference.

So why isn't it working? And what do I have to do to get the Gutsy boot disc to be able to boot to its desktop?

---

### Post by Xiong Chiamiov on 2008-04-03
VESA is the crappy driver that'll pretty much run anything.
It's possible that your monitor doesn't support a low res like 640x480 (I'm assuming it's an lcd).  If you know that a certain resolution works (1280x1024, etc), then try running it at that res and get back to us.  I know I had some problems with getting things to work on my monitor until I actually got it installed.  You can also try the alternate install cd if you can't get that to work.

---

### Post by swarup on 2008-04-03
> **Xiong Chiamiov said:**
> VESA is the crappy driver that'll pretty much run anything.
It's possible that your monitor doesn't support a low res like 640x480 (I'm assuming it's an lcd).  If you know that a certain resolution works (1280x1024, etc), then try running it at that res and get back to us.  I know I had some problems with getting things to work on my monitor until I actually got it installed.  You can also try the alternate install cd if you can't get that to work.

My monitor is actually one of the old type--the ones that are real heavy, and about 18 inches deep. The current resolution settings in XP are 800 x 600.  And I just now dialed up the the resolution in XP to test it, and it goes up to 1280 x 1024-- although when I do that, the writing on the desktop is very, very small. But I'll try changing the resolution, and see if that works.

I had tried playing with the driver, changing it to something that said it was for the Intel 845G card. But that also didn't help. Let me go and see if increasing the resolution works.

---

### Post by swarup on 2008-04-03
I just tried changing the resolution. Actually, for the Dell Monitor E772c, the resolution is fixed in Gutsy's setup disc as 640 x 480 @ 86 hz. It cannot be changed. Unless of course one changes the choice of monitor, which doesn't make sense to do given that it is printed on the back of the monitor that it is the E772c. 

Please let me know if you have any further suggestions. You did mention the alternative cd. I would have to download that, but I could. Never had to use it before. I would have thought this Dell would be a pretty straightforward install, as I've already done it on several Dells and never had any problem.

---

