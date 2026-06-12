---
title: "Ethernet on Ibook"
date: 2008-03-28
forum: Apple PPC Users
---

### Post by Thespiain on 2008-03-28
I have just installed Ubuntu 6.10 edgy on my ibook and i can't seem to use the ethernet connection. I plug in the cable, and use automatic configurations. I enable the wired connection, and it doesn't work. I have no idea how to tackle this as i am very unfamiliar with Linux. Thanks.

---

### Post by stream303 on 2008-03-28
If you bring up a terminal, can you restore operations by bringing up the ethernet interface manually?

```
sudo ifup eth0
```

That is, if eth0 is your ethernet card, it might be eth1

You may have to go back into your network settings.

Absolute worst case - try reinstalling with the ethernet cable connected beforehand...

---

