---
title: "Desktop hangs if I try to enable desktop effects"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-05-02
I have a machine with an old nvidia TNT2 M64 card in it.  I went into the restricted drivers manager and ticked the NVIDIA accelerated driver (legacy cards) and after a reboot, it appears to be running (it is now ticked as in use)

I then went to the desktop effects system preference and clicked on the enable button, this causes the panels to disappear and the button to grey out, leaving a busy cursor, and there it sits (I left it many minutes).

I opened a text console, logged in, and ran top, and nothing seems to be happening, everything is just idling.  So I switched back to the graphics console and it was still hung with the busy cursor (and most of the screen did not repaint).  So I use ctrl-alt-bspace to get my desktop back.

I have tried this twice, it just hangs each time.

Is my graphics card too old?  Is it a bug?

---

### Post by dstew on 2007-05-02
One possible fix is to disable composite video. It takes up a lot of processing time in the card, and if you don't need it (for hooking up to a TV video input), you should disable it. You can disable it by editing the xorg.conf file. Make a backup, then use the text editor nano.```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old
sudo nano /etc/X11/xorg.conf
```Add these lines to the file, and exit with saving using control-X:```
    Section &#8220;Extensions&#8221;
Option &#8220;Composite&#8221; &#8220;Disable&#8221;
EndSection
```Reboot.
But, again, maybe the card/driver combination can't manage the effects. I don't really know.

---

