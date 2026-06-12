---
title: "Using custom modelines and options in xorg.conf - how safe it is?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by tanelt on 2007-06-17
In order to get a desired resolution and a refresh rate I will probably have to spend several weeks trying out custom modelines and other related options. Therefore, I want to ask how safe this process is.

Is i possible to damage your monitor and or graphics card while trying them out?


Also, how safe is trying out options such as this one?
```
Option "UseEdidFreqs" "False"
```

Is it completely safe to experiment or am I risking damaging my hardware?

---

### Post by alienexplorers on 2007-06-17
If you set you refresh frequency to high you can damage the monitor.  I usually check the monitor specs before trying any experimental modelines.  So far I have not blown anything up so I figure this added safety measure works.

---

### Post by Reugen on 2007-06-17
It shouldn't damage the hardware, the only risk you have with that i believe is if you set a res/refresh to high for a crt and it isn't made to block a res thats too high.  As far as software goes you have a high chance of ruining your gui.  althought it can easily be rewritten by doing sudo dpkg-reconfigure xserver-xorg.  I would actually recommend that for making changes to your config file since it will guide you a bit.

---

### Post by tanelt on 2007-06-17
> **alienexplorers said:**
> If you set you refresh frequency to high you can damage the monitor.
By "refresh frequency" do you mean the HorizSync and VertRefresh values in xorg.conf?


Last year I bought a CRT monitor that cost me 640$ (probably one of the last great CRT monitors ever made) and I don't want anything to happen to it.

---

### Post by phr0ze on 2007-06-17
Yes, And modlines set those too.

Why are you playing with these? Is it not giving you the max resolution of your monitor?

Can you post the monitor section of your xorg? And tell us what resolution you are really after?

---

### Post by John.Michael.Kane on 2007-06-17
This may help if you hand editing your Xorg configuration.

Make sure you know your CRT/LCD specs or have the manual on hand
[http://ubuntuforums.org/showpost.php?p=1691257&postcount=2](http://ubuntuforums.org/showpost.php?p=1691257&postcount=2)

---

### Post by tanelt on 2007-06-17
[QUOTE=phr0ze]Why are you playing with these? Is it not giving you the max resolution of your monitor?[/QUOTE]
The maximum resolution of my monitor is 2048x1536, which is obviously too much for everyday use on a 21" monitor. It seems to display this resolution correctly, but I only use it for watching 1080p movies.

[QUOTE=phr0ze]Can you post the monitor section of your xorg? And tell us what resolution you are really after?[/QUOTE]

All the information and discussion about it is in this thread: [http://ubuntuforums.org/showthread.php?t=444222](http://ubuntuforums.org/showthread.php?t=444222)

The resolutions I need:
**1280x960 @ 120Hz  -- for everyday usage** and for watching 720p movies
2048x1536 @ 75 Hz -- for watching 1080p movies

^ Both work perfectly in Windows.


SD-Plissken: Thanks for the link, I'll take a look at it.

---

### Post by RedSquirrel on 2007-06-17
This might help as well:

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

