---
title: "Irritating screen resolution problem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by SlyReaper on 2008-01-29
I've been running ubuntu gutsy on my desktop just using the live CD.  The reason I haven't taken the plunge and installed it is because it refuses to detect the proper resolution of my monitor.  My monitor is 1680x1050.  Is that really such an unusual screen size?  Anyway the best it can do is 14**x1050 which leaves black bars on either side of the screen.  Also, the black bar on the right actuallys hides part of the desktop - the thing that shows time and date at the top is obscured, for instance.

I've managed to get ubuntu gutsy runing perfectly well on my laptop with 1280x800 resolution, so I know it's perfectly CAPABLE of detecting widescreen resolutions.  But why won't it do so for my desktop monitor?

For reference: It's a CIBOX 22 inch 1680x1050 LCD monitor, using a VGA input.  Graphics card is a Radeon HD2600 Pro.

Any help would be appreciated.

---

### Post by subpar on 2008-01-29
Do you have the resolution inside of your xorg.conf? Copy and paste your /etc/X11/xorg.conf. It could be as simple as just adding the right resolution inside of it, and then restarting X.

---

### Post by benfindlay on 2008-01-29
Have you tried running ```
sudo dpkg-reconfigure xserver-xorg
```

This will allow you to reset-up your display options. When you get to the stage marked simple, meidum and advanced, choose medium and you can choose which resolutions to show in your display options as well as choosing your preferred resolution

Hope this helps!

---

### Post by SlyReaper on 2008-01-30
OK thanks, I'll give it a try.  I suppose I'll actually have to install ubuntu on my HDD to do this, right?

---

### Post by JoshuaRL on 2008-01-30
Yeah.  Conversly you could try that in the LIve CD, and just realize that it won't last.

And I think it's:

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by sailor2001 on 2008-01-30
sudo dpkg-reconfigure -phigh xserver/xorg   to change resolution

---

### Post by SlyReaper on 2008-01-30
AARRGGHH!!!

OK I finally installed it on my system.  On startup, it told me it couldn't detect my screen or graphics card or something and was going to start in safe graphics mode (800x600 res).  I installed the ATI restricted drivers, installed updates to gutsy and various other things.  Now, after it starts up, the desktop goes green.  All the colours are corrupted or something.  On the bright side, it now lets me select 1400x1050 resolution, which is STILL not what my screen resolution is!   How annoying!

Also, my internet connection keeps cutting out in gutsy.  Shows as still being connected to my wireless router, but won't connect to any web pages.  It's not the router's fault because my other computer has no problems connecting when this happens.

:confused:

Is there any way I can fix this, or should I write it off as a lost cause and reformat the partition?

---

### Post by SlyReaper on 2008-01-30
Sorry to bump my own topic, but it's sinking into unread pages...

---

### Post by benfindlay on 2008-01-30
> **JoshuaRL said:**
> Yeah.  Conversly you could try that in the LIve CD, and just realize that it won't last.

And I think it's:

```

sudo dpkg-reconfigure xserver-xorg

```

Indeed it is, I made a typo!

---

### Post by SlyReaper on 2008-01-30
Well I've tried that xserver-xorg thing with no joy.  It gives me a bunch of configuration options, and then proceeds to ignore them (at least it does regarding the display ones).

---

### Post by ugm6hr on 2008-01-30
If Ubuntu is starting in "safe" mode - the ATI driver has obviously not worked.

I would recommend trying the very latest ATI driver.  There is a how-to in the Multimedia stickies forum.  Or just follow the link in my signature below "Graphics Card Driver" - Envy is an unofficial script that will install automatically for you.

---

### Post by wolfen69 on 2008-01-30
> **SlyReaper said:**
> Well I've tried that xserver-xorg thing with no joy.  It gives me a bunch of configuration options, and then proceeds to ignore them (at least it does regarding the display ones).

to choose which resolution, you must use the space bar to select which one(s) you want.

---

### Post by SlyReaper on 2008-01-31
Well here's a conundrum.  My internet connection held out long enough for me to download Envy, but it WON'T hold out long enough to let Envy do its thing.  

I've also tried downloading the driver from the ATI site.  I found a command in another thread to get a .run file to work.  Anyway, my screen is so small that the "next" or "okay" button is hidden below my screen.  Pressing enter instead results in a message that something beginning with V is missing.

*twitches* It's laughing at me.  It's doing supid things on purpose!  I..... will..... DEFEAT IT!!! *throws computer out the window, goes outside and stamps on it a few times*

---

### Post by JoshuaRL on 2008-02-01
Well, check this out.  In most Linux (including Ubuntu) you can hold ALT and click anywhere on a window to grab it.  Then you can move it.

If you still get that error then post it here.

And just so I'm sure I'm helping correctly, could you post the output of:

```

gksu gedit /etc/X11/xorg.conf

```

---

