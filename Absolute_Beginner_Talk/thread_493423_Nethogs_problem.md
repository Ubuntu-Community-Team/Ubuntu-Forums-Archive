---
title: "Nethogs problem"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-07-05
It used to work fine but now when I run it I get the following error:

**ioctl failed while establishing local IP**

---

### Post by brk3 on 2008-01-22
same problem. any ideas?

---

### Post by Sliph on 2008-01-24
I'm struggling with the same problem. Can't find anything useful on the subject on google either. Would appreciate some help on this, as I need an app to figure out what's eating my upload.

---

### Post by brk3 on 2008-01-24
specfiying the network interface worked for me:

sudo nethogs eth1

---

### Post by Sliph on 2008-01-25
Thank you, i can't believe I overlooked something that simple. I even tried sudo nethogs device eth1, but stupidly enough i didnt try without "device". THanks again, it worked for me now! :)

---

