---
title: "tightvnc can't find fonts?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by toblix on 2007-10-27
After upgrading to 7.10 freeNX no longer worked, so I decided to install tightvnc, but I got the message:
> Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

So I edited* /usr/bin/vncserver* and inserted this line:
> $fontPath = "/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/75dpi/";
I still get the same error message, though. I've noticed that in all examples, the font path has the 'X11' and 'fonts' parts reversed, but in my installation, '/usr/share/fonts/X11/' was where I found the files. Anyone know what I'm doing wrong?

Also, is there a console file editor that's a bit more... conventional than vim?

---

### Post by pasta514 on 2007-11-07
thanks for catching the swich between X11/fonts and fonts/X11...


This is what worked for me:
> sudo vim /usr/bin/vncserver
```
$fontPath = "unix/:7100";

$fontPath = join ',',qw(
/usr/share/fonts/X11/misc
/usr/share/fonts/X11/100dpi/:unscaled
/usr/share/fonts/X11/75dpi/:unscaled
/usr/share/fonts/X11/Type1
/usr/share/fonts/X11/100dpi
/usr/share/fonts/X11/75dpi
);
```

It got rid of that error message, although this might just be the default path anyway??

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

