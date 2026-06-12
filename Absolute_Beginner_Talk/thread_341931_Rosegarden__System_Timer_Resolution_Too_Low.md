---
title: "Rosegarden:  System Timer Resolution Too Low"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by nayo on 2007-01-19
I'm about to cry believe it or not.  It's just that I bought this 400 dollar machine mostly just to run Rosegarden (for me, a lot of money) and up comes "System timer resolution too low". Plus there's no sound.

The Rosegarden FAQ mentions some work-arounds, the only one of which I haven't tried is recompiling the kernel.  I have no idea what that means and don't understand really what I have read about it.

Has anybody figured this program out and how to run it on Ubuntu 6.10?

The  search I did in this forum didn't help when I followed the described paths.

---

### Post by nayo on 2007-01-20
is it a good idea to recompile the kernel for a beginner in Ubuntu 6.10?

---

### Post by eric71 on 2007-01-22
You can get a user made realtime kernel for edgy here:
[http://devlinuxbr.codigolivre.org.br/](http://devlinuxbr.codigolivre.org.br/)

Or, there is a lowlatency kernel available for feisty.  I've read some posts where people have installed it and it works fine in edgy.

I've used the first solution in edgy and it solved any complaints from Rosegarden, and am now using Feisty with the lowlatency kernel also with no problems.

---

