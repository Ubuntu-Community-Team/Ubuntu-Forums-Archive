---
title: "Gparted dapper LiveCD problem"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-04-15
My mate is trying to resize his XP partition so he can install Dapper. However, he gets a message saying something about root user and gparted being a weapon of mass destruction!

How can he get around this problem?

Cheers

---

### Post by Legionox on 2007-04-15
He can get around this problem by starting a Terminal Window (Applications -> Accessories -> Terminal) and typing in ```
sudo gparted
```

---

### Post by xpod on 2007-04-15
```
gksudo gparted
```

"gksudo" for gui apps:D

EDIT:[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by spamzilla on 2007-04-15
*edit*

We didnt see xpod's message. He's trying that now.

Ok that worked, however he doesn't see his partitions now :/

This is what he see's (see att. image). how can he fix this?

thanks mate :)

---

### Post by spamzilla on 2007-04-15
Ok he tried 'gksudo gparted' but he still cannot see the XP partitions :/

---

### Post by TwistesdTexan on 2007-04-15
Most likly he can't see the partitions because the drive is active. Goto Qparted.com and you can download a live disk for editing partitions on a hard drive. I don't know if this is the proper way to do things but it will work. Be sure to Defragment your hard drive about 2-3 time before repartitioning your hard drive if you intend on dual boot.

---

### Post by spamzilla on 2007-04-15
The only thing with that is that he hasn't got any blank CD's! Is there another way to fix this problem without having to download another partitioning program?

---

### Post by laidback on 2007-04-15
You can run it from the Ubuntu Live cd if you have it.

---

### Post by spamzilla on 2007-04-15
> **laidback said:**
> You can run it from the Ubuntu Live cd if you have it.

But the thing is, it doesn't work properly. Look for the attachment a few posts up to see what he gets when he opens it.

---

### Post by n3tfury on 2007-04-15
> **spamzilla said:**
> But the thing is, it doesn't work properly. Look for the attachment a few posts up to see what he gets when he opens it.

time to pony up for some blank cd's then.  i've had similar problems in the past with gparted being a part of a live cd and not a standalone.

---

### Post by Bartender on 2007-04-15
> **n3tfury said:**
> time to pony up for some blank cd's then.  i've had similar problems in the past with gparted being a part of a live cd and not a standalone.

So have others.  

IMO download [GParted]("http://gparted.sourceforge.net/livecd.php"), not QTParted.  GParted seems to be easier to use than QParted.  I don't have personal experience with QT, it just seems that folks have come to this forum with QT problems that went away when using GParted.

---

### Post by STREETURCHINE on 2007-04-15
i second the gparted live cd ,it works well have had some problem with gparted on the live cd,

---

