---
title: "Live CD - Nvidia driver question"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jcconnor on 2007-02-20
I have an nvidia video card that the Live CD (obviously) doesn't deal with.  I have 2 questions on being able to get a Live CD to boot properly with it (using Ubuntu, of course):

1)  When I boot a standard Ubuntu Live CD can I simply type apt get install nvidia-glx and then type startX at the command prompt after I get the can't start X screen??

2)  How would I (I am a new-user, so be gentle) create a Live CD that already has the nvidia driver and the proper xorg file?

Thanks,

John

---

### Post by po0f on 2007-02-20
jcconnor,

You can boot the live CD with the NVIDIA card in, you just have to change something.  When the live CD gets to the menu, hit F6 to change kernel parameters.  there should be some words at the bottom of the screen that look like this:

```
[font="Courier New"]quiet splash --[/font]
```

Add "agp=off" to those parameters so it looks like this:

```
[font="Courier New"]quiet splash agp=off --[/font]
```

Now press enter to boot it.

---

### Post by jcconnor on 2007-02-20
Thanks.  I tried that

F6 at boot, typed in ***quiet splash -agp=off --***

same thing.  X session failed to launch.

BTW, I also tried ***apt get install nvidia-glx*** but it wouldn't work - some error about apt.

I'm sure it's something I'm doing wrong :( .

Any others??

John

---

### Post by po0f on 2007-02-20
jcconnor,

You weren't supposed to type in "quiet splash"; those should just be the last of the default options.  And it's "agp=off", **not** "-agp=off".

Is this a motherboard with an integrated Intel graphics chip?  Try "noload=intel_agp noload=agpgart agp=off" as kernel params.

---

### Post by jcconnor on 2007-02-20
Thanks - sorry.  Holding my hand through this is probably just gonna get your hand sweaty!!

:) 

John

---

### Post by po0f on 2007-02-20
jcconnor,

So, did it work?  Don't leave me in suspense here.  ;)

---

### Post by jcconnor on 2007-02-20
Sorry for the delay - I tried it (actually, you were right on - the nvidia is an add on - I have an on-board intel) and same thing - X failed to start.

Really, the only time I need it is if I need to do something like repartition my /.  Other than that - it's not that big a deal.  Well, it kinda is - I wish there was an option to load the nvidia drivers on startup.  I hope they add that to Feisty - it will make it much, much easier for normal folks - ok, nearly normal.

Sorry!!

John

---

### Post by po0f on 2007-02-22
jcconnor,

If your original issue is repartitioning your hard drive, you could always just install [gparted](http://packages.ubuntu.com/edgy/gnome/gparted).  Saves you the hassle of a reboot; just don't mess up.  ;)

```
[font="Courier New"]$ sudo apt-get install gparted[/font]
```

---

