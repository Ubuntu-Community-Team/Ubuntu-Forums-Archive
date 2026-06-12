---
title: "Help blender"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by newhen on 2006-05-29
Hi, I'm pretty much a noob at linux even though I've had it for awhile. anyways the question is **blender 3d is installed on my machine its on my applications menu too but when I try to start it up it wont start  up. anybody have this problem or knows how to fix it? anything will help thanks](*,) **

---

### Post by newhen on 2006-05-29
bump

---

### Post by aysiu on 2006-05-29
Type this command in the terminal and post the output back here: ```
blender
```

---

### Post by newhen on 2006-05-29
> Type this command in the terminal and post the output back here:
Code:

blender


admin@defualt:~$ blender
Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window
admin@defualt:~$
admin@defualt:~$

---

### Post by aysiu on 2006-05-29
Based on [this Google search](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=Xlib%3A+extension+%22GLX%22+missing+on+display+%22%3A0.0%22.+site%3Aubuntuforums.org&btnG=Search), it appears to have nothing to do with Blender but a lot to do with your xorg file or your video drivers.

Follow the link I posted and see if any of those threads help you.

Are you able to launch other graphical applications, and it's only Blender that's giving you trouble?

---

### Post by newhen on 2006-05-29
only blender

---

### Post by newhen on 2006-05-29
I dont really understand what xorg is?

---

### Post by aysiu on 2006-05-29
[QUOTE=newhen]I dont really understand what xorg is?[/QUOTE] There's a file: /etc/X11/xorg.conf

It's the xorg.conf file that lives in the X11 folder inside of the etc folder.

It contains all the specifications for your video card and monitor. If you have special drivers for ATI or NVidia, those specifications are also in the xorg.conf file.

When I Googled your error, I didn't see anything about Blender, but I did see a lot about ATI or NVidia drivers.

---

### Post by Kilz on 2006-05-29
Blender requires a 3D accelerated graphics card that supports OpenGL. do you have such a card?

---

### Post by MetalMusicAddict on 2006-05-29
Also are you running Compiz and XGL?

---

### Post by heartbeat on 2007-05-16
do you really need Compiz and XGL?

---

