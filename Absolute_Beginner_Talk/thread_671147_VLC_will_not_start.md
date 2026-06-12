---
title: "VLC will not start"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ljsmithx on 2008-01-18
I tried starting VLC and it would not open, so I went to the terminal and typed "vlc"
and I get this:

"starting VLC root wrapper... using UID 1000 (levi)
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 476 error_code 11 request_code 147 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"

I have uninstalled it and then re-installed it and the same error, I have also tried to "vlc --sync" and same thing. 

Any ideas?

---

### Post by ljsmithx on 2008-01-18
Anyone? I love VLC and I want to watch movies in it.

---

### Post by fyo on 2008-01-18
Try the following thread and the solution presented there:

[http://ubuntuforums.org/showthread.php?t=671065](http://ubuntuforums.org/showthread.php?t=671065)

It seems to be working for some, but unfortunately not me.

---

### Post by ljsmithx on 2008-01-19
I've downgraded the xorg thing but that doesn't work:(

Has anyone had this problem and has figured it out?
If so I would love to know about it because VLC is the only media player I like...

I wonder what could cause it to do that:confused:

---

### Post by kaptainlange on 2008-01-19
I was able to duplicate your problem, and then noticed there was an update available to xorg that just appeared within the past few hours.  Applying that update seems to have fixed it.

---

