---
title: "Fglrx problems?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Gleep on 2007-04-25
Still trying to get Beryl working on Feisty, still can't get things quite right.

After following this: [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#video-acceleration-introduction](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#video-acceleration-introduction) (for ATI) I get this:

$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

And

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


I have no idea what this is trying to tell me :( Please can someone help?

I had Beryl up and running on Edgy by the way, so I do know it's possible with my card etc.

---

### Post by 007Bond on 2007-04-25
All you have to do is DL a program called Envy and install the ATI driver and it will work!! BTW what card do you have?

---

### Post by Gleep on 2007-04-25
Ah I used Envy before, seem to remember that worked. But I thought I did have the driver...

I'm using an ATI Radeon 9550

---

### Post by Praill on 2007-04-26
Wow, I followed the feisty guide to a tee, just as I did the edgy guide. I could not get direct rendering to work.

This envy program seems to have done it for me. Great, great program. I might have to donate to the developer :)

---

