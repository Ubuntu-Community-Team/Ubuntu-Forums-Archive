---
title: "VLC media player decided to stop working..."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-18
I do not approve of its decision.

Seriously, it just randomly stopped working it won't open or anything. I've tried complete removal and then installing, but that doesn't help.

---

### Post by Thelasko on 2008-01-18
Does it not open if you double click on a video file or when you open it from the application menu?  Try opening it from the application menu.  It might just be an incorrect setting.

---

### Post by 449 on 2008-01-18
> **Thelasko said:**
> Does it not open if you double click on a video file or when you open it from the application menu?  Try opening it from the application menu.  It might just be an incorrect setting.

It does not open for anything.

---

### Post by nikoPSK on 2008-01-18
try a clean reinstall of vlc please. :)

---

### Post by benerivo on 2008-01-18
Have you tried uninstalling vlc, and then removing ~/.vlc and also /usr/lib/vlc and then reinstalling?

---

### Post by stimpack on 2008-01-18
Same here, only been applying normal updates and installed kde4 since it last worked.

When started from the cmdline it gives.

```
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 632 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

---

### Post by stimpack on 2008-01-18
Ok, I posted in the 1st thread in search results, if I had read the second thread 1st I would have fixed it. Apologies :)

[http://ubuntuforums.org/showthread.php?t=670942&highlight=vlc](http://ubuntuforums.org/showthread.php?t=670942&highlight=vlc)

---

### Post by p_quarles on 2008-01-18
See:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)
[http://ubuntuforums.org/showthread.php?t=671419](http://ubuntuforums.org/showthread.php?t=671419)

---

