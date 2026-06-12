---
title: "Several questions"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Velotix on 2006-11-07
Xubuntu 6.10 is up and running for the most part, but there are a couple of issues:

1) Xubuntu appears not to have detected my SoundBlaster X-Fi sound card and has instead loaded the on-board audio on the motherboard as the audio device. How can I fix this problem? Do I need a driver for the sound card?

2) Similarly, are there any specific drivers for an nVidia GeForce 7900GS graphics card? Is the driver on the nVidia web-site sufficient?

3) On a minor note, I have been experimenting with quicklaunch icons on the top bar and seem to be unable to give them specific icons, so they now all have the same unhelpful generic icon. How can I fix this? (It's probably very simple, I know.)

4) A related command-line issue: how do you get a file to load with a specific program via the terminal? This would allow me to use Python 2.4 or Python 2.5 depending on which was necessary at any given time.

Thanks, folks. ^^

---

### Post by Perfect Storm on 2006-11-07
**1) Xubuntu appears not to have detected my SoundBlaster X-Fi sound card and has instead loaded the on-board audio on the motherboard as the audio device. How can I fix this problem? Do I need a driver for the sound card?**
Try turn off your onboad soundcard in the BIOS

**2) Similarly, are there any specific drivers for an nVidia GeForce 7900GS graphics card? Is the driver on the nVidia web-site sufficient?**
Ubuntu uses the open source driver (nv) by default. If you want to use close source driver from NVidia it's possible.

---

### Post by po0f on 2006-11-07
Velotix,

If you need a script to launch with Python 2.5, set this as the she-bang line:
```
#!/usr/bin/python2.5
```
By default, python is a symlink to python2.4, so if you install Python 2.5, you'll have to get to it via the full path.

---

### Post by Velotix on 2006-11-07
> Try turn off your onboad soundcard in the BIOS

Will do.

As for the graphics card, if the generic driver is sufficient then I'll have to mess around with xorg.conf, right? (My ideal resolution and refresh rate settings appear to be 1280x1024 @ 75Hz on this monitor, and I'm pretty sure this isn't how it's configured right now (an apparent limitation of Xfce from the looks of it).

> By default, python is a symlink to python2.4, so if you install Python 2.5, you'll have to get to it via the full path.

symlink = shortcut, yes?

I should have mentioned I was using the terminal to load Python 2.5 via the IDLE interface (superflous though it may be, we also use it at uni so it'll make keeping in sync easier). You would be suggesting then that I edit the IDLE file itself (it's a .py) - perhaps make a special copy?

---

### Post by Perfect Storm on 2006-11-08
Well, symblink is stronger than a shortcut. [http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)



Do you have your monitor manual?

---

### Post by Velotix on 2006-11-08
> Do you have your monitor manual?

Hm. You will probably find this interesting, as I certainly do:

When I unpacked the monitor, I noticed that **there wasn't a manual**. Also, it had a European power supply socket. :-k (Fortunately, the computer shop had the foresight to include extra leads and adapters. ^^)

Later on, having realised that this monitor was not correctly configured, I figured I'd look for the model on ebuyer.com. I read the code on the side of the box and the brand name and put them into the search engine.

From my search: "IBOX L1952S" I received just one result: the **LG L1952S**. I'm guessing LG operate under a different brand name elsewhere in Europe, because it is indeed the exact same monitor in all but name.

Anyway, the monitor's specifications are [here](http://www.ebuyer.com/UK/product/115266).



As for your suggestion to disable the onboard audio, this was successful only in ridding me of that audio device and reclaiming some wasted CPU load. Xubuntu still isn't detecting my SoundBlaster, and I'm guessing this isn't exactly an uncommon problem.

---

### Post by Velotix on 2006-11-08
Ah. Found the problem, and it's the worst-case scenario. :/

[ If you look here](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix), you'll see that the X-Fi is unsupported and will probably remain unsupported for the forseeable future. And after all that effort to get hold of it, too. :(

However, I did notice something: that page hasn't been updated for 18 months. Is there a more recent version of the page or is that still the most up-to-date version of the system available?

Finally: any suggestions as to what I should do next? Restore the on-board audio? ^^

---

### Post by Perfect Storm on 2006-11-08
Well, you could try with;

<ctrl>+<alt>+<F1> (This will take you away from X (desktop and into  CLI (command line interface)).

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

to setup the right resolution.

---

### Post by Velotix on 2006-11-08
Interestingly, that had no effect on the xorg.conf file, and by that I mean it wrote an identical copy of the xorg.conf file I had before. I'm guessing I'll have to manually write to xorg.conf.

Before I do that, though (and I already have the modified file prepared), I need to know how to put things back if it doesn't work, seeing as if X is garbled I won't be able to do it from within.

Also, is there any way to quickly determine the optimum horizontal sync? I'm guessing if it's wrong then the screen will refresh very badly so that'll warn me.

---

### Post by Perfect Storm on 2006-11-08
I could not find anything in the link that reffering to your monitor's horizontal sync and vertical. If you can find it somewhere it will make things alot easier.

---

### Post by Velotix on 2006-11-08
Hm, now another minor problem has shown its face: when I restarted X, it seems to have loaded the incorrect keyboard layout; the default US map. I'd like my UK keybpard map back but I'm not sure how to do this in Xfce as it isn't in the obvious place.

---

