---
title: "poor image quality"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by aesthete on 2007-07-12
Hey guys, I'm completely new at this, so I was wondering if you guys could shed some light:

After several days (okay...weeks) of hard work, I finally managed to get ubuntu+beryl doing everything I want it to. But a few applications are looking extremely poor in image quality, most noticeably the Avant Window Navigator and Screenlets. The window decorations are all right, as far as I know, but probably not the best out there.

I took a screenshot--

[[IMG]http://newsboyhat.co.uk/wp-content/uploads/snapshot1.thumbnail.png[/IMG] ]("http://newsboyhat.co.uk/wp-content/uploads/snapshot1.png")

Can someone tell me what might be the problem? I can see web images fine--in fact, I looked at the screenshots on the screenlets website and the images look much, much smoother than the ones I have. I don't know if it's beryl or graphics card or what. Thanks so much!

---

### Post by loserboy on 2007-07-12
I can't really tell but doesnt it kind of look like you're running in 16-bit color?

---

### Post by aesthete on 2007-07-12
maybe... how can I change it to check? everything else looks all right, just those two applications, though :-S

---

### Post by DSn0wMan on 2007-07-12
Its usually listed in your /etc/X11/xorg.conf file

---

### Post by Blutack on 2007-07-12
From
[http://ubuntuforums.org/showthread.php?t=228266](http://ubuntuforums.org/showthread.php?t=228266)


You can change it in your xorg.conf file.


> To edit from within gnome run:

gksudo gedit /etc/X11/xorg.conf

To edit from a command line use:

sudo nano /etc/X11/xorg.conf

look at screen section for default depth and change it, 24 is the highest depth


Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
Monitor "Generic Monitor"
DefaultDepth 24

---

### Post by aesthete on 2007-07-12
Ok, I believe I changed it (yes, it was indeed at 16-bit). Now I assume it requires a restart for all the effects to change place. Thanks for all your help guys!

---

