---
title: "dirvers of video card"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by santiagorf on 2008-03-10
Hi,
I have just installed Xubuntu 7.10. When I went to "Screen and Graphics Preferences" windows to configure the screen, not only it didn't take my new screen configuration, but it also changed my graphic card to a generic one. How should I do to change the drivers of the screen/video card  properly?I also want to know if there is some way to detect my video card automatically since I don't know what model is it.
Thanks in advance!!
Santiagorf

---

### Post by taurus on 2008-03-10
If you don't know what graphic card you have, open a terminal and run this command.

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by santiagorf on 2008-03-10
It tells me:
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

When I go to "screen and graphic preferences" to change the monitor and the generic driver to this one, It asks me to log off. to make the new changes; however, when I log on, I have again generic drivers for both screen &  video card.

---

