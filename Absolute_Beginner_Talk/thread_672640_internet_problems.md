---
title: "internet problems"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2008-01-19
after i browsed for sometime in ubuntu 7.10 it got disconnected suddenly while i am browsing(i ve been using it for a month without any problem).its been 2 days since there is disconnection and i cant connect it again.but the net works fine with windows.

---

### Post by eolson on 2008-01-19
Wired or wireless?

Laptop?

Did it happen to coincide with doing some updates?

---

### Post by arvindenrique on 2008-01-19
its usb modem with a pc.i did nt do any update.i was just browsing

---

### Post by eolson on 2008-01-19
Do you get the network monitor icon.  If so, is it the monitor or the signal strenght bars?   what does it say if you left click on it.

I'm assuming by USB you mean your wireless?

---

### Post by y-lee on 2008-01-19
That happened to me once using dapper. Typing the  following into the terminal fixed it for me

```
sudo ifdown eth0
sudo ifup eth0
```

Don't know if it will work for you but it is worth a try. 

Forgot to say replace eth0 with whatever you connect with.

---

