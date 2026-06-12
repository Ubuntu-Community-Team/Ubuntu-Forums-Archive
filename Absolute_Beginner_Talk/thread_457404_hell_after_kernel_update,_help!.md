---
title: "hell after kernel update, help!"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-05-28
after update to 2.6.20-16
the low latency kernel wont start
I have to manually start the generic one in grub

I get an error something about X server
my bets are on graphics drivers
my videocard is an nvidia gforce fx 5200

---

### Post by Jussi Kukkonen on 2007-05-28
> I get an error something about X server

Gmbrdilos, this is just not enough information...

---

### Post by petersjm on 2007-05-28
You've got the same card as me. I used to get a "failed to start x" thing until I installed a different graphics driver - can't remember from where; if I think of it I'll let you know.

In the meantime, do you mean you can't start x? If that's the case, login to the command line when you boot up and type **sudo dpkg-reconfigure xserver-xorg**. Follow the instructions and answer the questions (most can be left as default, but read them first). Then you should be back up and running - as long as that was your problem.

---

### Post by lazyart on 2007-05-28
me too, same vid card.  I'm using the old kernel until it sorts but, but I did see there is a new nvidia driver in the repos that matches the new kernel.

I hear the virtualbox doesn't like the new kernel either (needs a recompile).

---

### Post by Gmbrdilos on 2007-05-28
the generic works on mine the problem is just with low latency.
I'll be using this for the moment, whats the difference anyways?

---

