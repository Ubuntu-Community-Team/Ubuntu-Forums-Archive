---
title: "[SOLVED] aMule doesn't start :S"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-19
I just installed aMule and I also have ktorrent which works fine. When i started aMule for the first time it popped up a warning that this was the first time I'd started it and I was to go to...blah blah blah. I didn't read it, though now i was i had :/. The problem is aMule doesn't start when i click it and it doesn't show up in the system processes. Any ideas?
Thanks
Fraser

---

### Post by Hallvor on 2008-01-19
Try starting it from the terminal with ```
amule
``` and post the output here.

---

### Post by Fraser from Scotland on 2008-01-19
fraser@fraser-laptop:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 406 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
fraser@fraser-laptop:~$ 


thats what i got :S

---

### Post by Fraser from Scotland on 2008-01-19
bump :(

---

### Post by dank277 on 2008-01-19
I am an old user of aMule and I just had the same problem.  It seems that this was broken with a recent update to the Xorg files.  The ubuntu repository people have already have put a new update out to be installed.  I fixed this same issue by just using update-manger.  There should be new Xorg files to be updated.  After install, close apps, restart Xserver (ctl-backspace), and it should be good to go.

---

### Post by Fraser from Scotland on 2008-01-19
yeah that was it! thanks buddy!

---

