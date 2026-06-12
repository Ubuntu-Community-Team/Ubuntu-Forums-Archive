---
title: "A bit of trouble removing Ubuntu ):"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by sliggy on 2008-03-24
It's been a sad time. I need to remove Ubuntu off my mac due to my large files D:

So I deleted the Ubuntu partition with Disk Utility, and the Linux Swap partition is still there, but when I try to delete it, it says Done, but the Swap patition is still there. If I try to resize the OS X partition, it gives me the error in the picture below. Any ideas on how to fix this?

---

### Post by afterkelsen on 2008-03-24
The OS X disk utility probably have issues understanding the Linux partition types. Boot you machine on an Ubuntu Live CD and use GParted to remove the partitions.

That is, once in the Live CD environment open a terminal and type:
```
sudo gparted
```

---

