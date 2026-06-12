---
title: "Hard drive question"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by hrlslcbr on 2006-07-25
Hello. This is my first post on this forum and wanted to say hello to everyone :) .
I've installed ubuntu succesfully on a second partition on my hard drive, and I've had no problems (yet!) other than my X-Fi card that doesn't work... (not ubuntu's fault, I know).

One thing I've noticed is that when I reboot my computer, I hear a sound from the hard disks, the same I hear when I power down the PC (a big 'click' as if they were stopping). Now, here's my question (finally :) ) Does Ubuntu make the HDDs stop spinning when restarting the computer? I ask, because when I reboot under windows, the HDDs keep spinning and avoid a start/stop cycle, which make HDDs die sooner...

Thanks in advance.

---

### Post by ironfistchamp on 2006-07-25
Not a clue for the hard drive bit sorry but what is a X-fi card and just wanted to say

Welcome to the Ubuntu forums :) :) :)

---

### Post by hrlslcbr on 2006-07-25
:) :) Thanks. An X-Fi card is a soundcard made by Creative, and unfortunately, there are no drivers for it.

---

### Post by hrlslcbr on 2006-07-26
Well. I did some tests myself and found that when restarting ubuntu, the hard drives are forced to stop and spin again, which causes them to die much faster. Is there any way to prevent it from restarting the drives?

---

### Post by hrlslcbr on 2006-07-29
Please, has anyone noticed this or it's just my computer that does that?

---

### Post by hrlslcbr on 2006-08-13
bump...
Anyone?

---

### Post by hrlslcbr on 2006-08-26
Well, after 5 consecutive posts and almost no one commenting on this thread, I've found a solution for this problem. I switched to PCLinuxOS, and it doesn't restart the HDDs every time I reboot my computer, so it's something just Ubuntu does (not sure if any other distro does it too). I'd recommend anyone that cares to make Ubuntu better, to fix this which leads to kill the HDDs much faster.

---

### Post by sysop on 2006-09-15
> **hrlslcbr said:**
> Well. I did some tests myself and found that when restarting ubuntu, the hard drives are forced to stop and spin again, which causes them to die much faster. Is there any way to prevent it from restarting the drives?

I've heard two sides to the "theory" (at this point for me anyway ;) ) that spinning the hard drive up and down is good or bad for your system. One states more wear and tear, another states power saving and less wear and tear. I'm confused! :confused:  What opinion do others have, and isn't the spin up/down the same as power off and on?

---

### Post by xpod on 2006-09-15
My mouse makes a silly clicking noise too...how can i stop that?:-\"

---

### Post by bulldog on 2006-09-15
> **xpod said:**
> My mouse makes a silly clicking noise too...how can i stop that?:-\"

That's not good,KILL IT.:lol:

---

### Post by Brunellus on 2006-09-15
> **hrlslcbr said:**
> Well. I did some tests myself and found that when restarting ubuntu, the hard drives are forced to stop and spin again, which causes them to die much faster. Is there any way to prevent it from restarting the drives?
the drives are being read/written to.  Ext3 is a *journaling* filesystem, which means that every so often, the current state of the filesystem is written to a special file (the "journal"). If the computer should crash before the filesystem can be unmounted cleanly, Linux simply finalizes the last write of the Journal the next time it starts up.  

The net effect is that it keeps your filesystem neat and clean in case of a failure.  Sitting around and waiting for an 80 gigabyte filesystem to fsck is as close as you can get to purgatory as you can imagine.

Does it increase wear/tear on the hardware?  Possibly.  I've not had any hardware failures that I can blame on the filesystem yet.

---

### Post by NT4usB on 2006-09-15
Thermal cycles kill hard drives (and electronics in general.)
If you're just turning them off and right back on it isn't going to impact their life.

---

