---
title: "how to fix refresh rate"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by fire_storm on 2007-04-21
Hi

i had some problems with the resolution and i fixed it useing "nvidia-settings" how ever this can't fir my refresh rate it used to be 60 but now it is 50...
i use nvidia 7600GS  XFX  on feisty


Thank you

---

### Post by blitzer on 2007-04-21
Depending on what Ubuntu your using go to >System >Preferences >Screen Resolution and choose 85hz at the minimum (the best for your eyes) :)      This all depends on if your video card drivers is set up correctly.  Xorg would be the last place to edit if all else fails.  Let us know how it turned out.

Blitz

---

### Post by fire_storm on 2007-04-21
i did but the max i get is 50 
any other way   =/

---

### Post by Talon2 on 2007-04-24
> **fire_storm said:**
> Hi

i had some problems with the resolution and i fixed it useing "nvidia-settings" how ever this can't fir my refresh rate it used to be 60 but now it is 50...
i use nvidia 7600GS  XFX  on feisty


Thank you

Same problem here:  My monitor needs a refresh rate of 60hz but Fiesty and the nVidia driver only give me the option of 50hz or 51hz (?!?).  At this rate the screen appears to be in interlaced mode... it is hard on the eyes.  Using "nvidia-settings" resulted in a xorg.conf that would not boot x.

I'm seeing reports similar to this all over the forums and I see similar bugs in launchpad but I have yet to see a solution.  As far as I'm concerned nVidia support is badly broken in Fiesty.

MSI 7600GS

---

### Post by funkychicken9000 on 2007-04-24
I have a similar refresh problem, but I'm not *entirely* sure it's a problem...

I have spend the last few hours tinkering with my xorg.conf to get things like dual monitors and mouse buttons working.  I've crashed X a bunch of times and it's been a steep learning curve, but I think I now get it.

I edited xorg.conf to set the refresh to 60 at the res I use for each monitor (nvidia-setting is, as I have discovered, absolutely useless as if you get it to write your xorg.conf it will just replace it with a very unintelligently generated one, so edit it by hand if you've changed the slightest part of it).  Now, if I go system>prefs>screen resolution the only option is 50hz, but I'm not entirely sure that means my screens are running at 50hz.  When i look in the on-screen displays, both say they are running with 60hz input signals, so I think the screen res dialog is lying, as it's screwed up.

Any way of independently verifying the refresh rates?

---

### Post by fire_storm on 2007-04-25
can any one help please, my eyes hurt have to increse refresh rate  *_________*

---

### Post by Footissimo on 2007-04-26
Had the same problem - not sure if it was just it was just being reported that refresh rates were so low or if they actually were - tinkering with xorg,conf didn't seem to help, though nvidia-settings did help.  Not sure if this is related, but I found a bigger problem in that any opengl games seemed to crash after a few minutes (at best) on Fiesty.  Back to Edgy and everything is hunkydory now...arrrg.

---

### Post by lukew on 2007-04-26
> **fire_storm said:**
> Hi

i had some problems with the resolution and i fixed it useing "nvidia-settings" how ever this can't fir my refresh rate it used to be 60 but now it is 50...
i use nvidia 7600GS  XFX  on feisty


Thank you

sudo dpkg-reconfigure xserver-xorg.

When you get to the part about monitor detection select Advanced. You can put in your frequency there.

---

### Post by u.b.u.n.t.u on 2007-04-26
> **fire_storm said:**
> Hi

i had some problems with the resolution and i fixed it useing "nvidia-settings" how ever this can't fir my refresh rate it used to be 60 but now it is 50...
i use nvidia 7600GS  XFX  on feisty


Thank you

This is a known bug on some hardware.

---

### Post by floke on 2007-04-26
If you open a terminal and type 'xrandr' it will give you information on this

---

### Post by u.b.u.n.t.u on 2007-04-26
For those interested, ideas for Gutsy Gibbon have opened and I made a related suggestion:

[http://ubuntuforums.org/showthread.php?t=423745](http://ubuntuforums.org/showthread.php?t=423745)

---

### Post by JohanL on 2007-04-26
There´s a thread, and a solution, here:

[http://ubuntuforums.org/showthread.php?t=417716]("http://ubuntuforums.org/showthread.php?t=417716")

---

### Post by u.b.u.n.t.u on 2007-04-26
It is broken, hence a Ubuntu development team assigned to work to fix this.

Ref:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731)

"Affects  	Status  	Importance  	Assigned To
edit 	package xorg (Ubuntu) 	Confirmed 	Critical 	Ubuntu X SWAT"

---

### Post by fujikofujio on 2007-04-28
> **lukew said:**
> sudo dpkg-reconfigure xserver-xorg.

When you get to the part about monitor detection select Advanced. You can put in your frequency there.

Thanks I have a samtron 76df crt and I tried your suggestion and it worked, had to google for the vertical and horizontal refresh rate for this model. I am now able to set the refresh rate all the way to 85hz for 1024x768.

:)

---

