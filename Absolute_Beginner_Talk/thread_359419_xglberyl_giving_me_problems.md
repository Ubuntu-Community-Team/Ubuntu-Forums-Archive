---
title: "xgl/beryl giving me problems"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by MicroChris on 2007-02-12
Hey guys,

I'm new to the whole XGL thing, just tried installing it the other day. After getting it installed and loading it up, it worked, however it would take forever to load a window, and it took text atleast 10 seconds to catch up from my keyboard.

I was told to put this into /usr/bin/startxgl:

```
#!/bin/sh
Xgl :**1** -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:**1**
exec dbus-launch --exit-with-session gnome-session

```

However, when I put 1 as the display, I'd get errors under 'fglrxinfo', and I believe that's what was causing the slowdowns. So I tried this:

```
#!/bin/sh
Xgl :0 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:0
exec dbus-launch --exit-with-session gnome-session

```

Which reflects my fglrxinfo in Gnome. But when I load up an XGL session now I get this:

```
root@ubuntu:/home/chris# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: (null)
OpenGL renderer string: (null)
OpenGL version string: (null)

```

Any clue as to why this would be going on? The system performance is back to normal, but the wobbly windows and all of that don't work.

I'm running an ATi Radeon 9600XT, with drivers installed and working correctly.

Thanks,
Chris

---

### Post by quark_77 on 2007-02-13
Hi MicroChris,

I have an ATI Mobility Radeon and had some strange problems setting up Xgl/Beryl (I presume this is what you have set up, following a tutorial on the internet?).

Your error could be caused from the use of dbus. I tried the setup you have, specifically dbus-launch etc and it simply crashed my system. The instructions I followed ([http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) and [http://wiki.beryl-project.org/wiki/Main_Page](http://wiki.beryl-project.org/wiki/Main_Page)) suggested this as a startxgl.sh script:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
exec gnome-session
```
Having said that, I'm not sure if dbus makes a difference, it simply did for me. When you set up the driver, did you configure it with aticonfig? The command recommended by the first of the above tutorials was:
```
sudo aticonfig --initial --overlay=Xv
```
Hope this helps, let me know if it makes a difference!

Good luck!

---

