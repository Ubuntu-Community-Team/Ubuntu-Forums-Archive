---
title: "VLC horizontal green lines?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Skyler0 on 2007-01-02
So in the top of VLC theres a few green horizontal lines at the top. It's really weird. I tried some other videos, and they didn't have it, but I played the video in Totem and the lines are gone.

Anyone know what's up?

Thanks.

---

### Post by Copperteeth on 2007-01-02
I have the same problem but in totem as well, vlc did the same thing to me on windows so i rarely used it. I was playing an avi file and the video quality looks poor. I will post a few screenshots to give an idea of what im dealing with right now.

[Screenshot 1]("http://img.photobucket.com/albums/v239/copperteeth/Screenshot-1-2.png")

[Screenshot 2]("http://img.photobucket.com/albums/v239/copperteeth/Screenshot-3.png")

Notice how theres image ghosting happening,

---

### Post by MkfIbK7a on 2007-01-03
wow very strange sadly i have no idea whats causing it :(

---

### Post by Skyler0 on 2007-01-03
Here's a pic of mine, it looks a litttle different, and I can't find another video that it does it with lol. Althogh I played that video before I formated and it worked fine in VLC. And like I said that video works fine in Totem so idk...

but heres the ss

[Screenshot]("http://img526.imageshack.us/img526/4223/greenbarshk6.png")

---

### Post by MkfIbK7a on 2007-01-03
lol abbot and costello i still cant figure out whats causing it

---

### Post by Copperteeth on 2007-01-03
could it possibly be due to the fact me and skyler are running beryl? I know that the gui initializez the graphics car, its prolly a stupid question but in the area of graphics and graphics cards ect i know verry little

---

### Post by MkfIbK7a on 2007-01-03
hmmm... i dont think that beryl would affect vlc in any way but you know anything is possible!

---

### Post by Skyler0 on 2007-01-03
I don't think so. I mean... maybe, but if I recall correctly, I had VLC with Beryl the first time, and VLC was working fine (and it was when I first watched that video clip)

Offtopic: 
and yes,... abbot and costello, love those guys. D downloaded like all the old videos of them just recently, haven't seen them in quite awhile (like  A&C meet frankenstein, and those kind lol)

---

### Post by aidanr on 2007-01-03
are both of you using xgl?

i had the same problem before with xgl, i don't have the problem with aiglx or the nvidia drivers

i used "mplayer -vo x11" as a workaround when i was using xgl

---

### Post by Skyler0 on 2007-01-03
Ah, and yeah XGL. I dont have the problem with any other video I tried though, so idk... but thx  Ill see if it fixes that one.

---

### Post by Copperteeth on 2007-01-03
ok so what do i do then?

---

### Post by aidanr on 2007-01-03
well if you have mplayer installed you can watch your videos by either typing
```
mplayer -vo x11 video.avi
```
or use gmplayer and  choose x11 as the video output in gmplayer's preferences

i don't have vlc installed so i don't know how to set the video output on vlc, have a look through the options and look for something to do with video output

---

### Post by Skyler0 on 2007-01-03
I try to run mplayer from the menu and it just kind of vanishes lol. looks like it comes up for a fractin of a second, but then poof. gone. :S

---

### Post by aidanr on 2007-01-03
run it from a terminal (applications->accessories->terminal->gmplayer) to see what error it gives

---

### Post by Skyler0 on 2007-01-03
gmplayer returns

```
sky@sky-ubuntu:~$ gmplayer
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
98 audio & 216 video codecs
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(<unknown>:26908): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
[skin] file ( /usr/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

```

---

### Post by Copperteeth on 2007-01-03
ok i got it working, i selected the proper video output in vlc's video output options and all is well now, thanks al lot.

---

### Post by Skyler0 on 2007-01-03
yay, lol, so simple ^_^

although i still dont know whats up with that error thing up there ... lol

and yeah it worked for me too :P

---

### Post by aidanr on 2007-01-03
cool, btw gmplayer is looking for a skin there, it doesn't come with one by default, afaik you have to download a skin from the website

---

### Post by Skyler0 on 2007-01-03
ah lol, doesn't come with one on default ... lol odd, ill look into it, thx

---

