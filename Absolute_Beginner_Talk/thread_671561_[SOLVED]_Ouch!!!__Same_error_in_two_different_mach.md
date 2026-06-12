---
title: "[SOLVED] Ouch!!!  Same error in two different machines!!"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2008-01-18
I can't open VLC anymore.. :(

> cosimo@cosimo-laptop:~$ vlc
VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 205 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
cosimo@cosimo-laptop:~$ 


Today a friend of mine wasn't able to open azureus having the same error message insufficient resources for operation!! 


This happened after the updates we had today...

Is anybody else having this problem?!?!!?


Help!!!

:(:(:(:(:(:(

---

### Post by ajgreeny on 2008-01-18
Refresh synaptic and run upgrade again, or use apt-get.  It was the xserver upgrade earlier today that did the damage, then was made unavailable, and then quickly put right with version xserver-xorg-core-2:1.3.0.0.dfsg-12ubuntu8.2.

---

### Post by Kosimo on 2008-01-18
> **ajgreeny said:**
> Refresh synaptic and run upgrade again, or use apt-get.  It was the xserver upgrade earlier today that did the damage, then was made unavailable, and then quickly put right with version xserver-xorg-core-2:1.3.0.0.dfsg-12ubuntu8.2.

Thanks so much.

Exactly, I did update and upgrade synaptic and I had another xorg update. After restarting my system everything is working fine again.... Fortunately...

Even if the fix was really fast (something nice) This has been a serious critical locker (bug).

---

