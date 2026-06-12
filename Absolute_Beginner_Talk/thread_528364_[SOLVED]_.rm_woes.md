---
title: "[SOLVED] .rm woes"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by polarDave on 2007-08-17
Hey all.  Yes.  I'm new.  Hopefully with a little time I'll be answering questions, not asking them.  But for now....

I'm trying to install RealMediaPlayer 10.  I downloaded the RealPlayer10GOLD.bin file.  I changed permissions to executable across the board.  Everything I do recognizes the file.  I try to run it w/ sudo ./RealPlayer10GOLD.bin and I get "sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory"  

I even tried chown to root, re-downloading, filing it in a /media folder, /Desktop and /etc.  Same result for all combinations of above actions.

Are there any other good .bin files I could try this process on?

Is there any problem with this file on Ubuntu 7.04 64 bit?

---

### Post by AlexenderReez on 2007-08-17
you can install real player easily using[ medibuntu repo]("http://medibuntu.sos-sts.com/") or use smplayer to play rm file:)

---

### Post by polarDave on 2007-08-17
Ok.  I got the medibuntu repo packages and they didn't seem to do anything.  smplayer only had a 32 bit version (x86), so I followed a post on installing Adobe flashplayer for the 64 bit OS [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)
which got flash working, and allowed me to use that RealPlayer .bin file.

Crazy, but this is what we need to do to stick it to Bill Gates.

The above link shows you to libraries that allow your 64 bit OS to emulate a 32 bit one.   (As far as I can tell)  That's a valuable tool until the software world catches up w/ the new hardware.

Alexender, how do I close this as resolved threat?  

THANKS!!!
~

---

### Post by Paul133 on 2007-08-17
For marking a thread solved, go to thread tools -> mark page as solved or something like that.

---

