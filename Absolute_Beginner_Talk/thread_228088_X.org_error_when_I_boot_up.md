---
title: "X.org error when I boot up"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by sharifi14 on 2006-08-02
Hey,

I'd installed Ubuntu on my system, and I'd used an AGP graphics card to speed up the installation off the LiveCD because it was going horrifically slowly off my onboard graphics.

After messing around with Ubuntu, trying to learn bits here and there, I removed the AGP graphics card, but now whenever I try to boot into Ubuntu, after about half-way through the startup process, it gives me some error about the X.org window system being corrupted, lets me read some random error message, then just dumps me into command line stuff!

I know it's a long-winded explanation but if anyone else has encountered any similar errors I'd seriously appreciate your explanation on how to get around this.

Cheers,
Alex.

---

### Post by avtolle on 2006-08-02
Try this at the command line: dipkg-reconfigure xserver-xorg, just hit enter to respond to any questions you don't know the answer to, (of course, if  you do know the answer, input that data), and when this finishes, enter reboot. Hopefully, this will take care of your problem.

---

### Post by ironfistchamp on 2006-08-02
That should be dpkg-reconfigure xserver-xorg    no I in there :p

EDIT: This must be done as root. If it complains about this put sudo at the beginning.

sudo dpkg-reconfigure xserver-xorg

---

### Post by avtolle on 2006-08-02
Ironfistchamp: good save, must be my fat fingers or something.:D

---

### Post by ironfistchamp on 2006-08-02
Hehe np. I always have probs with my R key. Cheap keyboard.

---

### Post by sharifi14 on 2006-08-04
Sweet, thanks a lot for all your help, I appreciate it loads. I'll give that a try next time I'm working on that computer.

Cheers,

Alex.

---

