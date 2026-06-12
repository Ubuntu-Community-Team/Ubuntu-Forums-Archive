---
title: "install mplayer"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-28
i'm tryin to install mplayer. i wrote ```
./configure --enable-gui
```, and ... no pb
when i typed make , everything was allright except that at the end it wrote ```
Gui/libgui.a(interface.o): In function `guiInit':interface.c:(.text+0xae0): undefined reference to `vo_setwindow'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```
same pb at make install
pls hlp

---

### Post by raffytaffy on 2006-06-28
why not use synaptic to install mplayer? enable all your repo sources and search for it..its there

---

### Post by x64Jimbo on 2006-06-28
[QUOTE=raffytaffy]why not use synaptic to install mplayer? enable all your repo sources and search for it..its there[/QUOTE]
Or even better, Automatix?

---

### Post by FredB on 2006-06-28
[QUOTE=x64Jimbo]Or even better, Automatix?[/QUOTE]

Better ? In order to get some mess in your distro ?

I installed Mplayer from Synaptic (universe repository) :

```

fred@fredo: ~$ mplayer -?
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv[:dev]>  select video output driver & device ('-vo help' for a list)
 -ao <drv[:dev]>  select audio output driver & device ('-ao help' for a list)
 vcd://<trackno>   play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>   play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <timepos>    seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *

```

It is a not too old version. And at least, I know it will work.

---

### Post by Apple 101 on 2006-06-28
[QUOTE=x64Jimbo]Or even better, Automatix?[/QUOTE]
Just what is Automatix?

---

### Post by FuzZy2006 on 2006-06-28
i searched in synaptic but didn't find anything. i checked all the repositories.

---

### Post by Apple 101 on 2006-06-28
Open Synaptic --> Search --> mplayer

You may need to enable searching of all of the repositories by clicking the Reload button.

---

### Post by taurus on 2006-06-28
[QUOTE=Apple 101]Just what is Automatix?[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

### Post by FuzZy2006 on 2006-06-28
nothing happens when i reload : 18319 packages before 18319 packages after. when I type mplayer it finds only KMplayer

---

### Post by Apple 101 on 2006-06-28
[QUOTE=taurus][http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)[/QUOTE]
Thanks taurus.  That's a great automatic install programme.

---

### Post by FredB on 2006-06-28
[QUOTE=FuzZy2006]nothing happens when i reload : 18319 packages before 18319 packages after. when I type mplayer it finds only KMplayer[/QUOTE]

Erh ?

It is in multiverse repository.

And I have it using mplayer in search box.

---

### Post by vvlaw on 2007-03-23
i tried to install mplayer.

but i got some problem like this:

libvo/libvo.a(video_out.o):(.data+0x20): undefined reference to `video_out_xv'
Gui/libgui.a(interface.o): In function `guiInit':
interface.c:(.text+0xa29): undefined reference to `vo_setwindow'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
vvlaw@vvlaw-laptop:~/tools/player/MPlayer-1.0rc1$ 

anybody knows what's wrong lead to this?

help me ,please :(

---

### Post by kaay on 2007-10-04
> **FuzZy2006 said:**
> CODE]Gui/libgui.a(interface.o): In function `guiInit':interface.c:(.text+0xae0): undefined reference to `vo_setwindow'
[/CODE]
This will work: before doing a 'make', do a 'make distclean'.

And for those wondering why anyone would compile from source with binaries available through apt-get, easyubuntu, automatix and other means; here's a killer reason: It WORKS BETTER.
I've noticed an improvement in h.264: the precompiled mplayer couldn't play HD (1280x688) movies at full speed on my system, but the one from SVN can, especially if used without GUI.
Perhaps the difference isn't that great, it could have just as well been some 2% over the CPU's capabilities - still enough to wreck things. Now it's ~98%

---

