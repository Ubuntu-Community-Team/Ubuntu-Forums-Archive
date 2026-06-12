---
title: "Screen size"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by katoconfused on 2005-12-20
I'm a complete newby at all this stuff, however I like to think that I learn pretty quick. I have just installed Ubunto onto my G4 and I screwed up several times in the process. Finally, after I burned three different CD's and reading most of the Ubuntu website, I managed to do it properly. 

During the process I screwed up the "screen resolution" part of the installation by failing to select the correct screen resolutions. Now I'm stuck with three choices (I guess the default) and they're all too small. I need 1280 X 854 for my Ti G4. Any idea how to fix this up? I'm a complete beginner in all this control panel stuff and to me, what you guys post is complete gibberish, but I'm persistent. Please try to write it in Grade 1 Ubuntu:)

---

### Post by HyperNewbie on 2005-12-20
[http://ubuntuguide.org/](http://ubuntuguide.org/)
beautiful guide.

if u someway screwed up your settings, try this in terminal:
```

sudo dpkg-reconfigure xserver-xorg

```

hope this helps in some way...or am i rambling?

---

### Post by frodon on 2005-12-20
Generally those problems are solved by setting the good horizontal and vertical refresh rates (correponding to your monitor specification) in your xorg.conf file.
All you need to know is here : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

