---
title: "ati monitor cable"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2008-03-31
When installing/configuring a video card, lets say an ATI radeon 9600XT, does it matter what type of video cable I use to connect my Monitors to the video card? 

I just ask that question because at work I am installing a NVidia Quadro FX1700 and I am having a bit of a problem. I also notice that I am using vga cables instead of the DVI cable. Would this cause a difference in how the system recognize the monitors? BTW I am using Fedora core 8 at work, ubuntu at home. 

Also when choosing my type of monitors, I do not have the entry that matches my current set of monitors "Benq FP202" maybe because it is a new version of monitors.... I do not know, but would generic LCD drivers work in this case instead? Of course, choosing the right natural resolution of the monitors?

Thxs thxs thxs....

---

### Post by Rocket2DMn on 2008-04-01
You should be able to switch over to using the DVI cables without a problem, that isn't something that gets specified to X, the video card usually deals with that itself.  The 9600 supports the restricted ati drivers - see [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
If the screen fails to show up, you can automatically configure X with
```
sudo dpkg-reconfigure xserver-xorg -phigh
``` then setup the restricted drivers (don't forget to restart X with CTRL+ALT+BACKSPACE).  If the autodetection fails, follow this thread to manually go about reconfiguring X - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

The correct resolution depends on the monitor of course, but you usually don't have to specify the model for X, generic works just fine as the long as the resolutions are correct.  The sync rates are typically detected automatically.

---

