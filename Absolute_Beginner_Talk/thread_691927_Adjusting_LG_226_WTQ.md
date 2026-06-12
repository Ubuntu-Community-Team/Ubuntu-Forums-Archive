---
title: "Adjusting LG 226 WTQ"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by satjat on 2008-02-09
I just got a new monitor, an LG 226 WTQ.
While it is working pretty good in windows I can't get it to a similar point in Ubuntu 7.10
What seems to be the difference is that in windows it was detected and some drivers had to be added, while in Ubuntu I have it as Generic WIdescreen 1680x1050 Panel

I use the nvidia driver and my card is listed as Generic GeForce 6800. If I try to use the nv driver it reverts to the nvidia one (when I reopen the Screens and Graphics window)

I don't know if there are so many differences between the nv and the nvidia.
The resolution I am using is 1680x1050 at 59Hz (it seems my card won't go higher for some reason) or 1440x900 at 62Hz (it has 62, 61, 52 but not 60)

The main problem is that colors are a bit dull and at the 1680x1050 there is some noticeable flicker, not visible in windows at 1680x11050@60 

Thank you all in advance

---

### Post by tyggna1 on 2008-02-10
I find the best way to get the Nvidia drivers to do what you want them to is to use nvidia's utility.  From the command-line, install the package nvidia-glx, and then type in ```
nvidia-glx-config
```
that'll let you use the latest and greatest nvidia drivers, and it'll do all the autodetection that it can (which will probably be roughly the same thing it does in windows).

Should that fail:  I am fond of re-configuring the xserver and letting it do all the redetecting.  The command to do that is:
```
sudo dpgk-reconfigure xserver-xorg
```

---

