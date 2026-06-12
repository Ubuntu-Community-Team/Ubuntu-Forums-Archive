---
title: "does this mean my ati drivers are screwed?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-21
john@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: (null)
OpenGL renderer string: (null)
OpenGL version string: (null)

After the last round of updates i found some videos played choppy on my pc.

So i assume the fglrx drivers aren't being loaded anymore

---

### Post by rene100 on 2006-07-21
I have the same thing plus :

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by avtolle on 2006-07-21
If, "after the last round of updates" you are referring to kernel updates, then if you had to install said drivers manually before, you will (as I understand the situation, not having this issue) need to reinstall them.

---

### Post by lime4x4 on 2006-07-21
i think it was the fglrx update cause shortly after that compiz stopped working as well...

---

### Post by Anduu on 2006-07-22
If you downloaded and installed the drivers from ATI's website you need to reinstall them....

If you are using the xorg-driver-fglrx from the repos you sometimes get the "Mesa" issue...if this is the case see here [http://www.ubuntuforums.org/showthread.php?t=143283&highlight=mesa+fix](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=mesa+fix)

---

