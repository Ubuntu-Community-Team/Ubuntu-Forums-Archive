---
title: "Mighty Mouse on ubuntu"
date: 2006-09-17
forum: Apple PPC Users
---

### Post by ZERO_SHIFT on 2006-09-17
I am planning to buy an Intel MacBook and install ubuntu on it. I was wondering whether the apple wireless(and/or wired) mighty mouse would work on a ubuntu running MacBook, as it needs drivers. Is it possible? Anyone tried it?

Thanks

---

### Post by munchbach on 2006-10-11
Both work fine.  Wireless BT Might Mouse as well as wired.  Right click is supported right out of the box.  Horizonal scrolling and the side buttons are the only thing that don't seem to work for me.

With a Bluetooth mouse run:

```
sudo hidd --search
```

In a terminal window then flip the discovery swich (on a mighty mouse it is the flap that covers the optical eye) open and wait about 20 seconds.

Andrew

---

