---
title: "Enabling S-Video output to my TV"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by soldave on 2007-09-02
Have just installed Ubuntu yesterday after being a user of Windows for over 12 years, so forgive me if my questions are a little simple.  I'm liking the clean setup though and trying to work my way around it.

Most things are relatively painless at the moment (except for Japanese input, but that's a point for another thread!).  However, I am experiencing one graphical problem.  I've got an Fujitsu-Siemens Amilo D 7800 laptop and the laptop has an S-Video output for connecting to a TV.  In Windows, I could just select TV as an output and have a computer output on both my monitor and the TV.  I also configured it so that when I played movies on the computer, they would be shown in full-screen mode on the TV.

In Ubuntu, I've not yet managed to sort out the S-Video connection.  Some sort of signal is getting to the TV, but it's completely scrambled and you can't see anything recognisable.

Thanks for any advice you guys can offer me in advance.  It's all very much appreciated:)

---

### Post by mocoloco on 2007-09-06
There's an article about the driver supporting it [here]("http://www.phoronix.com/scan.php?page=article&item=806&num=1").  You would want to use "sudo" in front of the "make install" commands.
Also there's a package in synaptic called "atitvout", that may be an easy way to accomplish the same thing, or it may be something different.  
I don't have a system I can try it on.

---

