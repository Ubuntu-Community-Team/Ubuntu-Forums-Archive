---
title: "Help! Can't find a way to select monitor and video card in Ubuntu 6.10"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Pri0n on 2006-10-18
I installed Ubuntu 6.10 yesterday.  Booted up fine.  Noticed that my screen was 1024x768 @ 60 Hz.  So I went into the Preferences menu to change my monitor so that I can specify a better refresh rate.

So I look... and look... and look.  Where the heck is the monitor icon so that you can specify your monitor (hardware manufacturer and model) as well as your video card?

The closest that I can get to this is the "Screen Resolution" icon (gnome-display-properties I believe) that allows me select the resolution and refresh rate.  However, the refresh rate is locked in at 60 Hz (can't changed it) because Gnome doesn't know what monitor I'm using.

When I installed Kubuntu the day before, I could easily change my monitor type and video card.  Once I had done so, I could go into gnome-display-properties and access higher refresh rates.  But for the life of me, in Ubuntu 6.10 I can't find this menu icon ANYWHERE under preferences, or system tools.

Is this icon normally stored in the preferences menu?  Or can anybody tell me the command that will bring up the GUI application that allows you to select your monitor vendor and video card type?

Thank you.

---

### Post by CatKiller on 2006-10-18
I haven't used Edgy yet, so I don't know what GUI tools are available. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` will let you configure X's display from the command line though.

---

### Post by ReaderRat on 2006-10-18
Try this: ```
sudo dpkg-reconfigure xserver-xorg
```

EDIT: Late Again !!

---

### Post by Pri0n on 2006-10-18
Thank you.

I tried the command: dpkg-reconfigure xserver-xorg

It did allow me to go through the prompts and auto-detect my video card (correctly).  It tried to detect my monitor (Optiquest V75) but couldn't.  It then allowed me to specify the maximum refresh rate for my "generic" monitor, which I did. 

After I was done, I restarted X-windows but it still didn't allow me to access a higher refresh rate than 60 Hz.  (even though during the dpkg-reconfigure, I specified that my "generic" monitor had higher refresh rates than this)

So I manually edited /etc/X11/xorg.conf and scrolled down to the section that defined my monitor.  I used google to find the settings that are correct for my monitor (because I know that incorrect vertical and horizontal refresh rate settings can damage your monitor) and entered them in xorg.conf

I then re-started X-windows (CTRL + ALT + Backspace), and now was finally able to increase the refresh rate from 60 Hz to 85 Hz.

Its odd however that I have to do this manually.  In all other Linux distributions that I've tried, there is a "display properties" settings that allows you to specify what video card and monitor you use, and this in turn allows higher resolutions and refresh rates from being accessible.  (Otherwise, they are grayed out in the menu and you can't select them at all)

Working at 60 Hz was giving me eye strain.  So I was quite glad to finally be able to bump it up to 85 Hz.

In Ubuntu, shouldn't there be a menu item under system | preferences that allows you to specify this?  Like I said, I'm running 6.10 beta so I'm not sure if this is a bug or not.

---

