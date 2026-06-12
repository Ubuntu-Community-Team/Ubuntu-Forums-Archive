---
title: "KDE problems post Beryl and Wine installs"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by RAMpire on 2007-04-04
Hey all,

   Really new to the Linux thing; have the 965 chipset, so have been struggling to get anything installed on my machine.  I finally downloaded Feisty 7.04 beta, and all was well.  Shortly after the install, I decided to download and install the Beryl and Wine packages.  I got lost halfway through the Beryl setup, as I wasn't aware of where the scripts that I was being to told to write were supposed to go, decided to teak a short break from the process and check out wine.  I tried to open one of the Wine icons (sorry, but I don't remember which one), a black window opened up, went full screen, and all I was left with was a blinking cursor.  

   At this point, I hit Alt+F2, logged in, and tried to start KDE by entering ```
exec startkde
```, which started to run, then booted me out, requiring me to login again.

   I logged in and entered ```
dpkg-reconfigure xserver-xorg
``` on a recommendation I received.  After updating my nVidia card driver, my next session started (with a brief nVidia splash screen before KDE's) and mostly worked- there were a few games that wouldn't play at all, and there were updates that wouldn't install correctly. I figured a restart might get everything caught up, but upon restarting, KDE wouldn't come up.  No splash screen, nothing.  I tried the same 'fix' again, but this time, nothing corrected itself.

   If anyone can give me a hand, I'd appreciate it.

edit: looks as though it has nothing to do with Wine (which makes sense).

---

### Post by RAMpire on 2007-04-05
Hey,


   I noticed I was doing things kind of stupid.  I went back in and typed in 

```
startx
```

and got the following error:

```
(EE)Failed to load module "wfb" (module does not exsist,0)
XIO: fatal IO error 104(connection reset by peer) on X server ":0.0" after 0 requests(0 known processed) with 0 events remaining
```

I then put in 

```
sudo startkde
```

 resulting in:

```
startkde: Shuttingdown. . .
Warning: connecting() failed: : No such file or directory
Error: Can't connect to kdeinit!
startkde: Running shutdown scripts. . .
xprop: unable to open display"
usuage: xprop [-options. . .] [[format[dformat]]atom]] . . .
```

Hopefully this sheds more light on the problem.

Thanks again!

Edit: Would I be correct in assuming that I messed up something with x when doing the Beryl setup?  I recall a hangup I had with the process where I was asked to restart x, but thought "x" was referring to "x as in ___".

---

### Post by RAMpire on 2007-04-05
Is there anyone that can help me on this?  Am I just stuck?

---

