---
title: "A question concerning Dual-Booting."
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by TheKittenEater on 2006-12-17
Hey all!

I decided to try to switch to Ubuntu, yet I'm not ready to fully switch just yet. I'd like to Dual-Boot both Ubuntu and Windows. 

So, I was wondering: Is it easier to install Ubuntu first, then Windows? Or the other way around.

Thanks,

- Craig.

---

### Post by aysiu on 2006-12-17
Windows first, always.

By the way, I would play around with the live CD for a couple of weeks before committing to a full installation--even a dual boot one.

Cautious is always good.

---

### Post by TheKittenEater on 2006-12-17
Great, thanks for the fast reply!

So if I create two partitions, install Windows on one, then Ubuntu on the other one, would GRUB start up at boot?

Or is there some procedure I need to do first?

---

### Post by aysiu on 2006-12-17
Ubuntu's default is to install Grub to the MBR (master boot record), and in 99% of cases, Grub will automatically detect Windows and add it to the boot menu, so you can at startup select (with the Up and Down arrows) which OS you want to boot to.

You may find this helpful:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by TheKittenEater on 2006-12-17
Thank you very much!

Gotta' love the Linux community! ;)

---

