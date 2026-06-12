---
title: "Java apps cause firefox to close all windows"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-04
Yet again, I bid you all good day,

I have installed the 64 bid version of edgy.  I reinstalled the 32 bit version of firefox so I could get macromedia flash apps to work.  I posted yesterday that I was (and still am) having problems getting the embedded mplayer to do anything useful.  It seems that any web page that would have triggered the quicktime or windows media player in XP, just gives me the mplayer logo where the video should be.

Now on top of that, I just discovered that any time I try to load a page with java on it, all my firefox windows instantly close.  I discovered this when I attempted to test my vcersion of java to see if it was the latest and greatest.  I then tried a couple of java games with the same result.

My gut tells me that trying to use a 32 bit browser on a 64 bit system is what is making all these things buggy, and some how all these things are related.  Since I started my ubuntu adventure on friday, this is about the only thing that I've fiddled with for more than two hours and haven't been able to make much progress on.  Otherwise, it has been a pretty easy transition.  Anyone have any suggestions?

Thanks to everyone for the help!
Brian

---

### Post by Spr0k3t on 2007-03-04
I'll agree with the fact that Java Applets (not to be confused with Java Apps) do cause problems in 32bit FireFox on a 64bit platform.  I'm not sure what the issue is, but the Applets I've built to test the 32bit work like a charm... so it must be some specific class file causing the crashes.  One way to debug is to launch firefox32 from the terminal and watch the output.

---

### Post by marmaladejackson on 2007-03-04
Yes, sorry.  I mean Java applets.  Ok launched firefox32 from the terminal and got this:

[B]brian@brian-desktop:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:31681): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
brian@brian-desktop:~$ [/B]

Seems to be a bunch of errors there, but I really have no idea what they mean.  Does it make sense to anybody?

-B

Oh yeah, even though I get all those errors, the browser window pops up just fine.

---

