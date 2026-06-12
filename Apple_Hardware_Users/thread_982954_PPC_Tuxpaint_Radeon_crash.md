---
title: "PPC Tuxpaint Radeon crash"
date: 2008-11-15
forum: Apple Hardware Users
---

### Post by Leslie Viljoen on 2008-11-15
Hi everyone

Tuxpaint is crashing rather extremely on my G4 Mac Mini - when I run it the whole X session closes and I get logged out. I have done a lot of work trying to track the problem down but there's little to go on. If I use a remote control GDB session I can watch what happens: first there are several permissions problems with devices - when all those get fixed, there's just a SIGHUP. 

The interesting thing is that if you set up a VNC server, you can run Tuxpaint fine on that computer - as long as the display is redirected to another computer. This makes me think Tuxpaint is triggering a bug in xserver-xorg-video-radeon. 

Is anyone else getting this problem with Tuxpaint? Please post, especially if your system differs from mine.

---

### Post by Leslie Viljoen on 2008-11-19
I have stepped through the source and discovered that a call to SDL.init on my Xubuntu 8.10 system causes a crash. I have confirmed this by making the call through Ruby:

> irb
> require 'sdl'
> SDL.init(SDL::INIT_VIDEO)

This could mean that NO programs making use of SDL will run. Fedora showed the exact same behavior when I had that installed.

Anyone out there able to run any SDL based program on Intrepid/PowerPC?

---

### Post by Leslie Viljoen on 2008-11-19
Woah, I feel as though I'm the only one working on this! Can you hear the echo in the empty room?

Anyway, the error seems to come down to this:
[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg198748.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg198748.html)

I think SDL will work with a newer version of directfb. I will have to compile it and find out. I seem to have 1.0.1-9.

This is what directFB is spitting out, even when running as root: 


   =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-09-12 20:02) 
(*) Direct/Memcpy: Using ppcasm_memcpy()
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Access denied!

     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-09-12 20:02) 
(*) Direct/Memcpy: Using libc memcpy()
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Access denied!

Error: I could not initialize video and/or the timer!
The Simple DirectMedia Layer error that occurred was:
DirectFBCreate: Access denied!

---

### Post by Leslie Viljoen on 2008-11-20
Testing work-around here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=342053](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=342053)

---

