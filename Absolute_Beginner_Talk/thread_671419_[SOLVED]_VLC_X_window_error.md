---
title: "[SOLVED] VLC X window error"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by MegaJim on 2008-01-18
When starting VLC from the menu, nothing happens.  Starting it from a console (either with no arguments or with a valid media filename) gives:

```

james@james-desktop:~$ vlc
VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 476 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
james@james-desktop:~$ 

```

However, other audio players and movie players are functioning without any problems!

I'm using dual nvida gpus in sli mode, with DRI enabled, any help would be appreciated :)

---

### Post by p_quarles on 2008-01-18
Did you run the update manager earlier today? If so, here's the problem:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

---

### Post by MegaJim on 2008-01-18
> **p_quarles said:**
> Did you run the update manager earlier today? If so, here's the problem:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

thats exactly the problem i guess :)

Thanks, I had actually just installed gutsy today, so the thought that it might be a bug with an update released today hadn't occured to me!

Thanks for the information, much appreciated.

---

