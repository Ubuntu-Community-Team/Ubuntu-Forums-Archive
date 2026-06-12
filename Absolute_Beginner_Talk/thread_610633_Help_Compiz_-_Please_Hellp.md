---
title: "Help Compiz - Please Hellp"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by HackMe on 2007-11-12
I USE UBUNTU 7.10 I HAVE INSTALLED NVIDIA DRVIERS IT IS IN USE ... WHEN I WRITE IN TERMINAL COMPIZ I GET THIS ...


igor@igor-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
[SIZE="4"]**/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format**[/SIZE]

WTF ???

---

### Post by overdrank on 2007-11-12
Hi and what is the model of the nvidia card and did you use the restricted drivers?

---

### Post by HackMe on 2007-11-12
I HAVE NVIDIA FX 5500 my driver is enabled ... (Its In USE)

---

### Post by AlexenderReez on 2007-11-12
any direct rendering.....?

> glxinfo | grep direct



[PHP]reez | @ aLeXenDeRReez | Mon Nov 12 | 21:32:04 | /home/reez | uptime: 44m 46s |
$ -> glxinfo | grep direct
direct rendering: Yes
[/PHP]

---

### Post by HackMe on 2007-11-12
[SIZE="5"]igor@igor-desktop:~$ glxinfo | grep direct
[COLOR="Black"]direct rendering: Yes[/COLOR]
igor@igor-desktop:~$ 

[/SIZE]

---

### Post by HackMe on 2007-11-12
ok i found the error i fix it and now all was ok :)

---

