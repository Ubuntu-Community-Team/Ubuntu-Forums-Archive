---
title: "VIA graphics and x11 OpenGL"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by sammi.jo on 2008-04-02
Hi, thanks for your patience with me! I keep having a problem getting games open - I've posted it in here because I still can't understand most technical stuff. 

I keep getting the error  X11 driver not configured with OpenGL - but I have no clue what to do!

I have a VIA graphics card, and I have no idea how to revert to a vesa driver (I tried installing another one) and I have no idea how to do this X11 stuff!

Please help!:confused:

---

### Post by zvacet on 2008-04-02
You can try with [this](http://ubuntuforums.org/showthread.php?t=485646&highlight=openchrome) or if that doesn´t work for you type in terminal

```
sudo dpkg-reconfigure xserver-xorg
``` 

and when iti s come to drivers select **vesa **and continue to the end.Aftr restart you will have basic graphic.

---

