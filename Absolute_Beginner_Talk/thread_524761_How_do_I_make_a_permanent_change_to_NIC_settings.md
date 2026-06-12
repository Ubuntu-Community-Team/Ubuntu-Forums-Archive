---
title: "How do I make a permanent change to NIC settings?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by shannonr on 2007-08-13
Each time I boot, I need to pop a terminal and run ethtool to set eth0 to speed 10 and duplex full so I can "see" the network.

Don't ask why -- suffice it to say I'm connecting to some crappy old switching hardware. :)

Anyway, what do I need to modify to set eth0 to speed 10 and duplex full permanently?

---

### Post by janipewter on 2007-08-13
```
mii-tool -F 10baseT-FD
```

Hope this helps.

---

### Post by janipewter on 2007-08-13
****, double post. Delete this.

---

### Post by shannonr on 2007-08-14
Thankyou that seems to have done it.

You're a champion!

Incidentally, does any one else think that these sorts of settings should be available in
System -> Administration -> Network?

"Network" seems like a rather deceptive name for that utility. Perhaps "IP Settings", since that's all it does?

---

