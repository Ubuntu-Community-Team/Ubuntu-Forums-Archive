---
title: "Install trouble with Sony VAIO PCG-R505JLP"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by skywire on 2007-11-24
Hi Community,
This is my first post as a newbie. I'm having trouble putting Ubuntu on my elderly(circa 2001) backup PC, a Sony VAIO PCG-R505JLP laptop (Intel 82815 chipset, 382MB RAM and 15GB hard drive). I downloaded the ISO and wrote a boot disk which checks OK on the boot menu CD checker. But the program won't install/start from the normal boot option or from the OEM option. It only starts in safe graphics mode. That ran through disk partitioning with no apparent trouble and launched in safe graphics mode with its limited screen that doesn't show the full window's content. That's the only mode that runs. I need to get the full-screen mode going. Right now all I get is a lot of optical drive activity, some chopped up  theme music, and finally a dead black screen.

I would be very grateful for a solution from anyone with experience loading Ubuntu on VAIO R505 laptops. I'm trying to convince myself that I should switch from WinXP on my primary computer (HP ze2000 laptop) by testing Ubuntu on my backup. It's not a happy result so far. Thanks in advance to whoever bails me out of this fix.

Desperado Dave

---

### Post by infurnus on 2007-11-24
you need to resetup x properly run
```

sudo dpkg-reconfigure xserver-xorg

```
Go through pick the correct res and video driver. You were using vesa before (safe graphics) if you cant find a specific match you can use vesa then install the correct drivers for the video card once inside the OS and try again.

---

### Post by noremac on 2008-01-02
I am having the same problem on my Vaio r505je. About a 1 inch boarder or black around the screen (which should be used, but isnt). I have been trying to get it working by changing modes in the xorg, but whenever I put in a new mode, it does not change the screen resolution at all. I ran the command given here and no changes occurred either.  
Any other recommendations?

---

