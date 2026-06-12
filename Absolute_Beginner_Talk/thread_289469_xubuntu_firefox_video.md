---
title: "xubuntu firefox video"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by sloggerkhan on 2006-10-31
Hi there. I'm used to ubuntu, but I installed xubuntu on a low end system for a friend. I can't get flash to work for the life of me. I have looked at all other documentation and followed it.

Heres's what happens when I run firefox and go to a website with embedded video (youtube, which works on ubuntu)

[B]dodosong@dewey:~$ firefox

(firefox-bin:5021): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 96 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/B]

I tried doing with --sync, but it just produced the same result.

---

### Post by -Phi- on 2006-10-31
It's a Firefox 2 bug. You'll be wanting this thread [http://ubuntuforums.org/showthread.php?t=286069&highlight=firefox+flash](http://ubuntuforums.org/showthread.php?t=286069&highlight=firefox+flash)

- Phi

---

### Post by sloggerkhan on 2006-11-01
Oddly enough, I'm not sure if that problem is related, but I got flash and video plugins (mplayer) working on xubuntu by making sure there was a copy of them in every firefox plugin folder. (usr/lib/firefox/plugins AND (adding them here is what seemed to really make a difference) /var/lib/mozilla-firefox) What is completely weird is that even though they work, if you go the menu in firefox2 (tools>extensions) it shows that none are installed. Pretty sure this method is somewhat hacky, and that the problem is somehow related to xubuntu (and maybe its window manager?) specifically. Anyhow, seems to work now, though some videos seem to be missing sound.

---

