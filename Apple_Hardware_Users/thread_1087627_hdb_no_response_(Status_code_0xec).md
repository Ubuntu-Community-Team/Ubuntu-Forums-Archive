---
title: "hdb: no response (Status code 0xec)"
date: 2009-03-05
forum: Apple Hardware Users
---

### Post by jeffadams78 on 2009-03-05
I've successfully gotten 8.10 installed on my emac, but every time it boots there is a delay, then it finally prints this message:

[a number, which I suspect is a timestamp of some sort] hdb: no response (Status code 0xec)

Then it continues booting fine.

Does anyone know what it's trying to do and/or how I fix it?  It seems like it is attempting something that times out.  I'd like to get it to skip that so it boots faster.

This does not appear to be related to the xorg.conf issues I originally had, but have since fixed.

Thanks,
Jeff

---

### Post by jeffadams78 on 2009-03-05
Hmm.  Two things jump out at me.

1) No one has responded.

2) If you google "ubuntu hdb" this post is the first hit.

Not promising :(.

---

### Post by jeffadams78 on 2009-03-05
OK some more research seems to indicate hdb is probably the device handle for whatever the second drive on my ide interface is?

Except that there isn't one.  I have an emac, which has two ide (is channel the right word?) channels, each of which is a normal IDE channel meaning it has master and slave, so I could have up to four drives theoretically.  One channel has my single hard drive on it (which shows up under /dev/hda, it has a pile of partitions as /dev/hda1, /dev/hda2, etc).  The other channel has my cdrom drive on it, which shows up as /dev/hdc.

So, it kind of makes sense that hdb doesn't respond... after all, it doesn't exist.  How do I make ubuntu quit trying to check it on startup?

---

