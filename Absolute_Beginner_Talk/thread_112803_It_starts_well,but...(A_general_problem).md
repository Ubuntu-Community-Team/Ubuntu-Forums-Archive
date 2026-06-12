---
title: "It starts well,but...(A general problem)"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by dimxanthis on 2006-01-05
Hi 
I am totaly new to Linux.A friend of mine passed me an Ubuntu cd and I eagerly tried it out,starting from the live cd.It boots just fine but,after the installation the sceen is full of nonesense stuff and a flood of colours.I have an AMD sempron 2800+
    ATI Radeon 9250 256M
    asus m\b
    512M Ram
I never tried to isntall Ubuntu prorperly
Is there an issue with sempron or my graphics card (or perhaps,my luck:confused: )?Is Ubuntu for me as well?

Waiting for a reply,I thank you a lot.

---

### Post by andrewsco on 2006-01-05
What version of Ubuntu do you have? Perhaps if it's an older version there might be a compatability issue? Maybe there are some drivers that you need to download for your graphics card? I once had a problem where in Win98 there was no problems with my graphics etc, although when i upgraded to XP pro, there were loads of extra drivers I needed to download. Perhaps this is the problem? 

Other than that I cant help much - perhaps check out your graphics cards site?

Andrew

---

### Post by carlosqueso on 2006-01-05
when you get all of that crap on your screen, try pressing Ctrl+Alt+F1 and see if you can get a terminal to mess with stuff.  There's also a way to to it at boot, but I don't really know because I went right with the install cd.

---

### Post by Omnios on 2006-01-05
It sound like a Xorg config problem with your monitor, I had a similar problem with my older box where the driver was trying to run the refresh rates to high for the monitor and the right side of the screen had line double faded images.

 My solution was to open xorg.cong and manualy lower the resfresh rates. 
```
sudo nano /etc/X11/xorg.conf
```

You can also use 
 
 ```
sudo dpkg-reconfigure xserver-xorg
```

 which a install like graphical set up for xorg.

  You can also cheack the proper refresh rates for you monitor agains what is in xorg.config but be weary of increasing refresh rates beyond what your monitor states it can handle which may result in damage to the monitor

 Also if you can get your xorg.cong post it here as someone may be able to help. 
 I had to put mine on a floppy before and post it here a long time ago

---

