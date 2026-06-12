---
title: "kubuntu live CD boots to command line"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2007-02-04
i finally got the kubuntu live cd to get past the loading, and now it is in command line, how do i get it to go into the real interface

---

### Post by k1001001 on 2007-02-04
It's not Kubuntu Server Edition is it?

---

### Post by notquitehere188 on 2007-02-04
dont think so, it had no lamp option, also, wouldnt kubuntu server edition be a little odd, since the only difference between kubuntu and ubuntu is the interface and applications

---

### Post by shareMenaPeace on 2007-02-04
What happens if you type

```
startx
```

---

### Post by notquitehere188 on 2007-02-04
a huge error ending in "fatal IO error 104..." i can copy it out if it would help

---

### Post by shareMenaPeace on 2007-02-04
Yes, past the terminal stuff here (highlight the terminal text rightclivk and choose copy)

---

### Post by notquitehere188 on 2007-02-04
if only i could, but i am on a different comp since i cant do anything there
also, in the thing where you reconfigure xorg or something, how do you unselect an option

now, the error
xauth: creating new auhority file /home/ubuntu/.serverauth.6517
xauth: creating new authourity file /home/ubuntu/.Xauthority
xauth: creating new authority file /home/ubuntu/.Xauthority

X window system vrsion 7.1.1
release date....(this stuff looks to just be info about xwindow)
(==)log file: "/var/log/xorg.0.log", time...
(==)using config file: "/etc/x11/xorg.conf"

(EE) VESA(0): Set VBE mode failed!

fatal server error
AddScreen/ScreenInit failed for driver 0

XIO: Fatal IO error 104 (connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining



i tried the reconfigure xorg thing with ati drivers and that did not work

---

### Post by shareMenaPeace on 2007-02-04
Follow this thread
[http://ubuntuforums.org/showthread.php?t=124964&highlight=kubuntu+xauth](http://ubuntuforums.org/showthread.php?t=124964&highlight=kubuntu+xauth)
Try 
```
sudo apt-get install kubuntu-desktop
```

---

### Post by notquitehere188 on 2007-02-07
well, it seemed to me that i would need to have kubuntu installed to do that, so i installed it with the text mode.  But when that boots, it gets to the end, then shows another loading screen and puts a green line and blue dots across the screen, not solid.  and now, when i boot the live cd i get the same thing.

the other problem is that i dont think it has drivers for my network card, since setup complained about that, so i dont know if i would be able to apt-get

---

