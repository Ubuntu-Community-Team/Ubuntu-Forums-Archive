---
title: "ca0106 sound card driver no longer working after upgrade from dapper"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by barbobot on 2006-10-25
I upgraded from dapper to edgy eft and now my sound card 

01:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at c400 [size=32]
        Capabilities: [dc] Power Management version 2

no longer works, 

I have had it working in the past following the guide at [http://ubuntuforums.org/showthread.php?t=19307](http://ubuntuforums.org/showthread.php?t=19307)

the problem im having now is when i try to modprobe the driver i get 
a bunch of unknown version and unknown symbol files from alsa

So, I tried to re-compile, im now getting a /lib/cpp fails sanity check error. 

i have tried linking /lib/cpp to the various c pre processors on my system none of them seem to work. 

I have also tried completely removing my drivers and reinstalling the kernel image. 

if anyone else knows of a good way to get this working I would appreciate it

---

