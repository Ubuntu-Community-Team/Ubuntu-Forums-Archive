---
title: "[SOLVED] tried to fix refresh rate and now resolution is wrong..."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by cifdtruckie on 2007-12-30
My monitor was flickering and I was unable to choose a higher refresh rate, so I used the guide at [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

When I rebooted, the refresh rate was fine, but I was locked into choosing a res of 800x600 or 640x480.  I usually use 1024x768.

I went into xorg.conf and removed 800x600 and 640x480 from the Modes line, so that only 1024x768 is present, but upon reboot I once again was stuck with the aforementioned choices.  I reverted to the backup copy of xorg.conf, deciding I could deal with flicker but not such a crappy resolution, but upon reboot the res problem still exists...

I had been mucking around in compiz earlier, and I hope that didn't screw anything up... 

Any suggestions?

---

### Post by eternicode on 2007-12-30
Backup your xorg.conf file and run

```
dpkg-reconfigure xserver-corg
```

The defaults the program gives you should be fine (basically just click {well, select} a bunch of "OK"s).  When you come to the screen that asks what resolutions you want to use, go through (with arrow keys and spacebar) and select all that apply to your screen (many options will not).  Once that's done, log out, restart the X server, log back in, and see if you can change the resolution.

---

### Post by cifdtruckie on 2007-12-30
ehhh... never mind... it was my fooling around in ccsm that caused the problem... at any rate, maybe someone having the same problem as me will stumble upon this and be able to fix it!

---

### Post by cifdtruckie on 2007-12-30
> **eternicode said:**
> Backup your xorg.conf file and run

```
dpkg-reconfigure xserver-corg
```

The defaults the program gives you should be fine (basically just click {well, select} a bunch of "OK"s).  When you come to the screen that asks what resolutions you want to use, go through (with arrow keys and spacebar) and select all that apply to your screen (many options will not).  Once that's done, log out, restart the X server, log back in, and see if you can change the resolution.

Thanks for getting back to me so quickly!!!  I am always in awe at the level of support I find here!
:) :)

---

### Post by eternicode on 2007-12-30
No problem...but look, I typo'd :mad:

```
dpkg-reconfigure xserver-**c**org
```

should be

```
dpkg-reconfigure xserver-**x**org
```

My bad!

---

