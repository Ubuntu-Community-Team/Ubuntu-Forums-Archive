---
title: "Ubuntu problem"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by driton on 2006-11-21
After formatting my C Windows partition, i resized it to try Ubuntu 24 gb for Ubuntu and rest for Windows XP PRO. I installed Ubuntu and when it asked for the swap partition, i made a partition that has 17 gb for Swap use. ](*,) 
Now I want to uninstall ubuntu and to install it again in proper way. Can somebody explain how to format hd from windows or ubuntu partition.
Thanks

---

### Post by NiklasV on 2006-11-21
You can use GParted on the Ubuntu Live CD or the GParted live cd to resize or and format your partitions. The swap should be around 1-2GB.

---

### Post by bulldog on 2006-11-21
Delete the swap partition and the ext3 which you have created.
From the unallocated space right click and choose new partition,make a swap 1GB and make the rest your / [root] partition.

---

### Post by driton on 2006-11-22
Thanks to all I solved the problem.

---

