---
title: "Installing xvid / video issues"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by Poisonsnak on 2006-04-30
Just installing/using kubuntu for the first time ever this afternoon and I'd like to get kaffiene to play files encoded with XviD.  I downloaded the codec at [www.xvid.org](www.xvid.org) and just looking at these requirements:

1.a/ Requirements
  -----------------
   - ANSI C compiler (gcc)
   - make (GNU make, BSD make, Solaris make)
   - a C library providing ANSI C functions like malloc/free/realloc
     and some other standard functions.
   - nasm on ia32 platforms for MMX/SSE optimized code.

makes me think this is harder than it should be just to install a video codec.

I used "sudo apt-get install gcc" and the same for make and now it complains "error: C compiler cannot create executables".

Anyway, I have a feeling I'm going about this totally the wrong way - isn't there some way to install xvid without having to compile it first?

Also, if it's relevant, I had to change my /etc/X11/xorg.conf to use "vesa" instead of "ati" for a video driver (using X850XT-PE PCI-Express) because with "ati" I would only get a command line interface and using "startx" would yield "fatal error: no screens found".

---

### Post by nalmeth on 2006-04-30
That is a lot harder than it should be, or [I]is
[/I]If you've just done a fresh install, pick up automatix or easy ubuntu to install restricted codecs not included with ubuntu
then you should be set!
EDIT: Look at installing the proprietary ATI driver if you're looking for some 3d action
It's all in the forums. Use the search dialogue

---

### Post by Thirsteh on 2006-04-30
Since you're probably going to be doing more compiling in the future, please save yourself the trouble of going through several compiler/library installations and do a 'sudo apt-get install build-essentials' :)

If you're not steadfast on staying with kaffeine, I'd like to recommend Mplayer, it's pretty easy to use once you get a hang of it, and in my opinion, it's **the** media player, with the ["essential codecs"](http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2) from their [website](http://mplayerhq.hu), this beast can play everything.

---

### Post by nalmeth on 2006-04-30
'sudo apt-get install build-essentials' --> 'sudo apt-get install build-essential'

commonly confusing newer users :)

Don't think you're going to have to compile everything, unless you want to. 
APT RULES

---

