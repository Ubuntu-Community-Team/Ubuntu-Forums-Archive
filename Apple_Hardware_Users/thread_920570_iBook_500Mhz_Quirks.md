---
title: "iBook 500Mhz Quirks"
date: 2008-09-15
forum: Apple Hardware Users
---

### Post by darkmatter21 on 2008-09-15
Hey people,

I'm running Ubuntu 8.04 on an iBook 500mhz dual USB model and there are a couple quirks about it I'm hoping to resolve.

The first one, is the ubuntu splash screen is a magic portal - the screen that would normally show the ubuntu logo and a progress bar during startup and shutdown shows some text initially, but then slowly distorts to eventually just show off a mass of color. I'm also noticing that if I switch to TTY8, it does the same thing. Does anyone know of a solution or where can I configure these video settings?

The second quirk is that if I start off with a fresh boot then put the computer to sleep and wake it up, tapclick becomes enabled - even though I disabled it in xorg.conf. Tapclick also become enabled if I restart X with ctrl + alt + backspace.

Any thoughts?

---

### Post by darkmatter21 on 2008-09-15
After some googling I discovered that the configuration file for usplash is stored at
/etc/usplash.conf

Adding the following lines to usplash.conf
```
xres=1024
yres=768
```

then running the command
```

sudo update-usplash-theme usplash-theme-ubuntu
```

fixed the splash screen. (Had to restart after that, just running usplash from the console didn't work.) I now get ubuntu and the loading bar in all it's ugly orange brown color scheme glory. Haven't seen it since 6.06 on the iBook...

This was the magic thread.
[http://ubuntuforums.org/showthread.php?t=616510](http://ubuntuforums.org/showthread.php?t=616510)

I still have the problem of the trackpad tap-click enabling itself after I suspend and resume. Any advice for that problem is welcome.

---

