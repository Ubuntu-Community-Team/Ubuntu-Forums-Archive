---
title: "sound comes and goes"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2006-12-10
I have an Asus motherboard with built-in nvidia nforce2 audio. for some reason I get silence when I try to play any kind of media (streaming or a file on my hard drive). Later, all will work again even though I have changed nothing.

Most recently, I was trying to play a file through ryhthmbox and getting nothing. I closed ryhthmbox, tried kaffine and got sound -- then closed kaffine and opened ryhthmbox again and got sound there too. 

I changed no settings, just swiched between programs.

Anyone know what's going on?

---

### Post by wpshooter on 2006-12-10
Do you also have M/S windows on the box ?

If so, do you have any sound problems while in Windows ?

If you don't then I believe that would probably almost rule out hardware problems.

I would then think you might have had something go wrong during your Ubuntu install.  Or perhaps your hard drive is having problems and your programs are getting corrupted.  You might want to diagnose your hard drive.  You may also want to run memtest.

Good luck.

---

### Post by drphilngood on 2006-12-10
Try troubleshooting with this:

[Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449").

and post back if you still need help.

---

### Post by bcdeck on 2006-12-26
I think I found part of the problem. My sound preferences were set to autodetect for sound events, music and movies, etc. -- I set the various tabs to my specific hardware and everything is more stable.

But... 

I've also noticed that when I leave the volume setting in the gxine player low, it affects volume in Rhythmbox. Even if Rhythmbox volume is at max, I get silence if gxine volume is minimized -- whether gxine is running or not. I gxine is closed I have to open it and bump up volume to get sound. I'm checkig threads to see if this is addressed.

---

