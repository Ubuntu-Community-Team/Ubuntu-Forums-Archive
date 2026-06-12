---
title: "How do I install handbrake for Linux?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-19
I wanna install the program called handbrake!!! ANy ideas on how to install it?

---

### Post by T700 on 2006-07-19
Please see my sig for a link on installing anything.

Paul

---

### Post by pnutzh4x0r on 2006-07-27
Someone had emailed me for help a few days ago, so I wrote a small howto to get HandBrake up and running on Dapper;

[http://www.nd.edu/~pbui/blog/tips_and_tricks_20060724-103000.html](http://www.nd.edu/~pbui/blog/tips_and_tricks_20060724-103000.html)

Good Luck.

---

### Post by jbird123 on 2006-08-05
There were two sets of compile errors that I had to resolve with HandBrake-0.7.1. The first seemed to be a configuration file error for the libhb package. I modified the file

HandBrake-0.7.1/libhb/Jamfile

so the line beginning with 'ObjectCcFlags' looks like the following. This text should all be on one line:

ObjectCcFlags $(LIBHB_SRC) : -I$(TOP)/contrib/include -I$(TOP)/contrib/mpeg4ip/lib/mp4v2 ;


Once this modification was made, 'jam' got through much more of its compilation process. It stopped again, however, complaining about an 'faac' incompatibility. I'm not sure, but I think that 'faac' was installed by Automatix on my system. Anyway, the fix was straight-forward:

> sudo apt-get remove faac

This removes the 'faac' package. 'jam' completed successfully after that. Once Handbrake was completely built, I just re-installed the 'faac' package. The Handbrake program is statically linked, so over-writing 'faac' should do no harm that this point.

By the way, the compiled version I created with this method was 25 percent faster than the pre-compiled handbrake executable I found on the net.

---

### Post by stmiller on 2006-08-22
Jbird123: Thanks for your help! This should be a sticky.

Edit: I had to install the x264 development package, and copy the libx264.a file from /usr/lib/ to the contrib/lib directory of the Handbrake folder. For some reason, Handbrake didn't fetch that library.

---

