---
title: "Booting from a copied partition"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ppatalano on 2007-08-28
So, I was running GParted Live CD and copied my linux partition to an external hard drive. I returned to my computer about 20 minutes later and forgetfully deleted the linux partition on my internal hard drive. I cannot copy the partition back to my internal hard drive for some reason. Is these anyway to boot this copied partition off of the external hard disk?

---

### Post by notwen on 2007-08-28
Have you tried recreating the partition and C&Ping it back onto the freshly created ext3 partition?  You will also need to make sure the new partition has the boot flag.

---

### Post by ppatalano on 2007-08-28
For some reason it won't let me copy the partition that way either. I'm just going to do a fresh install and import all my files that way. Thanks for your help.

---

### Post by notwen on 2007-08-28
You should have been able to mount your new partition and your USB drive in a LiveCD session, oh well. Have fun w/ your fresh install. =]

---

