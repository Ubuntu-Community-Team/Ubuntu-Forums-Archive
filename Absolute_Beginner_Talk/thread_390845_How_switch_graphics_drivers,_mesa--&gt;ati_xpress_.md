---
title: "How switch graphics drivers, mesa--&gt;ati xpress 200"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Toadmund on 2007-03-22
Help!
I am trying to find something I lost, I found a terminal script on the forums here that showed the graphics card drivers installed and allowed you to pick one.

I am trying to use beryl, but all it does is spasm, then stops and returns to normal, no beryl.
I need to switch to my ATI driver, but I don't know how.

```
fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

How do I make this mesa stuff become ATI stuff.
I am spending WAY too much time trying to find out how to do this (2-3 days now)

---

### Post by jkeyes0 on 2007-03-22
Is it Envy you're looking for?

Here's the homepage:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by mikewhatever on 2007-03-22
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Toadmund on 2007-03-22
```
~$ sudo glxinfo | grep direct
Password:
direct rendering: Yes
```

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

```

Well, thanks, that stuff is an improvement, envy was so easy to download too!

However, when I try to start beryl, I still don't get beryl.

However, thanks, I am much closer now!

---

### Post by Waappu on 2007-03-22
Hi

You should install XGL and login to that session.
Follow this guide. Skip driver install part
[http://ubuntuforums.org/showthread.php?t=341149](http://ubuntuforums.org/showthread.php?t=341149)

---

### Post by Toadmund on 2007-03-22
How do I 'log into that session'?

---

### Post by Waappu on 2007-03-22
Hi

> When you come to the login screen you will have to go down in the left corner and click sessions and select Xgl from the list and click Change Session.

You can read same here after install part
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by jkeyes0 on 2007-03-22
If you've followed the guides, before you log into Ubuntu, there should be a button at the bottom left of the screen that says "Options". Click that, then go to "Sessions". One of the sessions should be named "Xgl", or "Beryl" (or whatever you named it by following the guides). Choose that one, then log in. It will ask if you want to make it the default, or just use it for this session. I usually don't make it the default until I'm certain everything is working.

---

### Post by Toadmund on 2007-03-22
It said /usr/local/bin/startxgl.sh unavailable or something, reverting to default.
I've got to go to work, bye.

I'll work on this problem again later.

Here is what I have in that file:
```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
exec gnome-session

```

---

### Post by lsutiger on 2007-06-01
I ran Envy, that didn't work. I tried several instructions, none work. Several are the same, and where I get an error is in the code:
sudo module-assistant build fglrx

[from this tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

The log is HUGE. I posted it on another post, but didn't get any response.

The error starts here:
```
 make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'     &#9618;                                        
                                       &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o                           &#9618;                                        
                                       &#9474; /usr/src/modules/fglrx/firegl_public.c:208: error: expected declaration    &#9618;                                        
                                       &#9474; specifiers or ‘...’ before ‘mlock’  
```
and continues with the "expected declarations" and other errors. It ends with 
```
 make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1              &#9618;                                        
                                       &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      &#9618;                                        
                                       &#9474; make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'      &#9646;                                        
                                       &#9474; make: *** [build] Error 2  
```

I just bought this laptop (Dell Inspiron 1501/ Ati Radeon 1150 Xpress) due to the fact of the success of getting the 3D working with this card.
I have scoured the forum, and I have yet to find the same error.

Please help! I don't want an expensive doorstop! :)

---

