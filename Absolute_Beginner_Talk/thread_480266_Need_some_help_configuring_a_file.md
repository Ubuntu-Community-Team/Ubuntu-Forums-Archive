---
title: "Need some help configuring a file"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by iver123 on 2007-06-21
Hi,

I have installed WoW now following this guide 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Now I've come to the "chapter" **Configuration** without problems, but now I want to change the DirectX mode till OpenGL mode.

I have found the "Config.wtf" file and I wonder how I shall add the text **SET gxApi "opengl"** in the file.:confused:

I'm not very good at using the Terminal yet so some help here would really help out!:D

---

### Post by sad_iq on 2007-06-21
Well open a terminal an type ```
nano .wine/drive_c/Program\ Files/World\ of\ Warcraft/Config.wtf
``` Write **SET gxApi "opengl"** then press Ctrl+X and enter to save!!!
 That Should be it!!!
 Or open the file with gedit and write  gxApi "opengl" than save and exit gedit!!!

---

### Post by iver123 on 2007-06-21
ok, great!:D Will try that out

Thanks!

---

