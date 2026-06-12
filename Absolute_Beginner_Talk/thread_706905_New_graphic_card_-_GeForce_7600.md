---
title: "New graphic card - GeForce 7600"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by stena on 2008-02-24
I have Ubuntu Gutsy on my desktop (dual boot with XP). Everything worked just fine until I installed new graphic card GeForce 7600. Ubuntu doesn't load at all in any mode (stops somewhere with graphic card driver loading). It works with old graphic card, but how to make it work with new one?

Thanks in advance,
Stena

---

### Post by JoshuaRL on 2008-02-24
Is the old card an onboard one?

You can always try the following from the Recovery Mode:
```

dpkg-reconfigure -phigh xserver-xorg

```

If that doesn't work we may need to do a little bit of manual configuration.

---

### Post by stena on 2008-02-24
Yes, the old one is the onboard one. And no, I can not reach console even in recovery mode. Ubuntu stops loading halfway, whichever mode i choose.

Dheers,
stena

---

### Post by mgranet on 2008-02-24
If you haven't already, you should disable your old card in the BIOS.

---

### Post by JoshuaRL on 2008-02-24
Yeah, try that and see what happens.  Does the screen just all of a sudden go blank?  If so, does the onboard card work after the screen goes blank?

You may have to hook the monitor back up to the onboard card to get this fixed properly.

Check out [this thread](http://ubuntuforums.org/showthread.php?t=570098) about this problem.  You may have to go and blacklist the driver for your onboard card before you can successfully install the Nvidia driver.

---

