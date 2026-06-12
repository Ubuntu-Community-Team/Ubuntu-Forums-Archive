---
title: "advice on combining JACK, low latency kernel, and me."
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-12-20
After three days of trying to get back into digital audio I think I require some advice.  Please bear with any noob related questions.  I'm running Gutsy on an AMD64x2

I am attempting to get JACK running and finally have an error I can't defeat on my own.

```

14:04:22.259 Patchbay deactivated.
14:04:22.318 Statistics reset.
14:04:22.377 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
14:04:22.541 MIDI connection change.
14:04:23.578 Startup script...
14:04:23.578 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
sh: artsshell: not found
14:04:23.782 Startup script terminated with exit status=32512.
14:04:23.782 JACK is starting...
14:04:23.782 /usr/bin/jackd -R -p512 -dalsa -dhw:0 -r44100 -p1024 -n3 -m
14:04:23.784 JACK was started with PID=8918 (0x22d6).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
[color=red]**cannot use real-time scheduling (FIFO at priority 10) [for thread -378348112, from thread -378348112] (1: Operation not permitted)**[/color]
cannot create engine
14:04:23.795 JACK was stopped successfully.
14:04:23.795 Post-shutdown script...
14:04:23.795 killall jackd
jackd: no process killed
14:04:24.004 Post-shutdown script terminated with exit status=256.
14:04:26.006 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

```

If I understand the situation correctly this error may be related to my kernel.

1.  If I install a "low latency" kernel, can I select that kernel from the grub menu thereby keeping my current 2.6.22-14-generic for normal pc use and create a new user specifically for audio needs for use with the new kernel?  I have no expereince with kernels or the grub menu  so this would be a new step in my linux experience.  I'm hesitant to get in over my head.  My pc is running sooo nicely right now :)  (thank you forum friends!)

2.  Is it more intelligent to use VM for an Ubuntu Studio install?  I've seen this suggestion but not to sound simplistic but this doesn't seem like it can beat the issues inhererent in the kernel that the VM runs on top of.

3.  I hope to get  a new sound card soon.  May this issue be resolved by a higher quality sound card (I'm using the integrated one for now while I figure all this out) or is that optimistic?

4.  Is this just an error I can work around with more digging or does anyone believe I may be on the right track with trying to integrate the Ubustu kernel?

5.  Does the Ubustu kernel have the I/O issues I've read about or am I out of date and simply trading out Gutsy's kernel for a low latency one will have no real issues?  Remember now, I'm 64-bit.

Any help is greatly appreciated!

---

### Post by il-luzhin on 2007-12-20
Wow, and all my tinkering has somehow disabled sound in flash.

wicked...

---

### Post by logos34 on 2007-12-20
As far as 1) goes, you want to install the 'linux-rt' pkg.  Make sure it installs the linux-restricted-modules for the -rt kernel because you may need to reconfigure the xorg file (sudo dpkg-reconfigure -xserver-xorg) just to get to the desktop to enable the restricted-driver-manager. (I think one of it's dependencies depends on it).  Adding another user sounds like a good strategy.  

The only major issue I'm having is that the -rt kernel does not allow me to hibernate or suspend. (Hopefully you won't have this problem).  The latest kernel update (-47, today) did not solve it for me. :-(

---

