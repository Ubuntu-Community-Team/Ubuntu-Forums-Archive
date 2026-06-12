---
title: "Powerbook G4 667MHz 512MB - no Mac OS installed"
date: 2008-07-25
forum: Apple Hardware Users
---

### Post by GhettoYhetti on 2008-07-25
I am trying to install Ubuntu 8.04 on my Mac and I am having zero luck getting X to start.  It does the "blink" thing approx 5 times then dies.  I have tried several hacks/mods to xorg.conf  . . . I thought this was going to be a slamdunk but I have to admit I need some help here.

I looked at the "Common PPC problems" page but I still have no luck.

Anyone?

---

### Post by stream303 on 2008-07-26
Be sure to see this recent thread even though it is for a G4 iBook:

[http://ubuntuforums.org/showthread.php?t=798974](http://ubuntuforums.org/showthread.php?t=798974)

The key issue is that you'll have specify your video card, and also your resolution.  Which machine do you have, as there are two different resolutions for the G4 667 powerbooks.  (1152x768 or 1280x854)  See everymac.com to help nail down the specs.

In either case, it sounds like you got the system installed but need to tweak.

The first thing I'd do is try starting up with the following special kernel paramaters.  You'll need to interrupt the second stage of yaboot boot: prompt by hitting -tab-.  From there, issue:

```
Linux nosplash video=radeonfb:1152x768-24@60
```

If your machine has the other resolution of 1280x854, then use that instead.

You'll want to make this change permanent in your /etc/yaboot.conf as shown in that thread, and be sure to make the system aware of it with

sudo ybin -v -C /etc/yaboot.conf

Be sure to see the main PPC faq.  It contains some good info on how to set your video driver for a radeon:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

The most important part being that you'll need to add a line to your /etc/X11/xorg.conf specifiying the radeon:

```
Section  "Device"
          Driver   "radeon"
```

I've seen a few threads about G4 powermacs, and should help provide some other assistance with the xorg.conf file...

---

### Post by GhettoYhetti on 2008-07-27
stream303

I gave all that a whirl . . . I am still not having any luck with X.  Just a blank screen . . . I let is sit for approx. 5 minutes with nothing happening.

Any other "tricks" up your sleeve?  I really do appreciate it.

---

