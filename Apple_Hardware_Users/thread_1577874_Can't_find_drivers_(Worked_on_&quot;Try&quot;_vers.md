---
title: "Can't find drivers (Worked on &quot;Try&quot; version)"
date: 2010-09-19
forum: Apple Hardware Users
---

### Post by Chuck26 on 2010-09-19
I installed Ubuntu today. Before I did that I was testing the "Try" version. I managed to pick up the wifi/wireless driver and some other thing in drivers. Now, I have installed it on my Mac and when I go on it, it says something about it can't get indexes and then it says it can't find any drivers.

Please help! - If you didn't read all of it. I'm using a Mac.

---

### Post by scullez on 2010-09-20
Try to enable your install CD in system > administration > software sources. This should work.
If you have wired connection to the Internet, you can download latest driver version for your wireless card via ethernet.

---

### Post by sikander3786 on 2010-09-20
> **Chuck26 said:**
> it says something about it can't get indexes

If that is the case, try changing the update server from System >>> Administration >>> Software Sources and

```

sudo apt-get update

```

---

