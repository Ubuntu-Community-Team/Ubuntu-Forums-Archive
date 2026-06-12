---
title: "Ubuntu Doesn't read all my RAM?"
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by underoathmatt on 2009-08-25
I installed Ubuntu Jaunty 32bit on my MBP 13".  When running in OS X my computer reads all 4GB of RAM I have installed.  However, when I boot into Ubuntu, my computer reads only 2.7GB of RAM.  Is this because I'm running a 32bit system? Or is there some other reason?  Thanks in advance.

---

### Post by tgeer43 on 2009-08-26
Yes, it is because you are running a 32-bit OS which while theoretically can address a max of 4GB, in real life the limit is closer to 3GB.

You can install the linux-server kernel to circumvent this limitation but that's as much as I can tell you. Try Googling 'Ubuntu 32 bit 4GB RAM' and you'll find plenty of info on this.

A better bet would be to switch to Ubuntu 64-bit if your processor supports it.

tgeer

---

