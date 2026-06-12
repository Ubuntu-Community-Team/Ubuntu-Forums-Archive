---
title: "One copy of Ubuntu should be enough"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by caughran on 2007-07-10
After installing Ubuntu, it checked for updates and installed a later version. Booting now gives me a choice of 4 Ubuntus (graphical / recovery for 2.6.20-16 and  2.6.20-15) and Windows.

There has been no problem with 2.6.20-16. How can I get rid of 2.6.20-15?

---

### Post by aysiu on 2007-07-10
Boot into the latest kernel (the highest number)

Go to System > Administration > Synaptic

Search for *linux-image*

Mark for removal all the earlier kernels

Apply changes

---

### Post by Skidpad on 2007-07-10
The best, short & to-the-point answer I've seen posted on here for old kernel removal.

Thanks for that aysiu (and all of your other helpful posts/blog as well).

---

### Post by caughran on 2007-07-10
Thanks!

There are a couple of packages also labelled 2.6.20-15, called *linux-headers*. Should these be deleted as well?

---

### Post by aysiu on 2007-07-10
> **caughran said:**
> Thanks!

There are a couple of packages also labelled 2.6.20-15, called *linux-headers*. Should these be deleted as well?
Yes

---

