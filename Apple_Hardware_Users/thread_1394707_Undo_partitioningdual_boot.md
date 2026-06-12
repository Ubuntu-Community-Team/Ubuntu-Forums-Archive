---
title: "Undo partitioning/dual boot?"
date: 2010-01-30
forum: Apple Hardware Users
---

### Post by msto on 2010-01-30
Hi,

I'm running OS X 10.5.8 and Ubuntu 9.04 on a Macbook 4,1, and I want to remove the Ubuntu partition so I can free up hard drive space. However, the linux swap partition is located in between the OS X and Ubuntu partitions, and GParted won't let me remove it when I boot from an Ubuntu Live disk, and OS X Disk Utility can't affect it either. I followed the dual booting instructions here, and I pretty much just want to undo all of it and get back to an OS X only machine. (Sorry, I tried Ubuntu out and had some fun, but it's not for me.) Any suggestions on how to do this? Thanks!

---

### Post by jbiggs12 on 2010-01-31
Going out on a limb here... I could be wrong, but I think that when you right-click on the swap partition there's an option to unswap/something like that... try clicking that and waiting for the operation to complete. Is there a key-symbol next to the drive when it shows up in GParted?x

---

### Post by msto on 2010-01-31
> **jbiggs12 said:**
> Is there a key-symbol next to the drive when it shows up in GParted?x

Yes, but only next to the swap partition.

---

### Post by linuxopjemac on 2010-01-31
If you select that swap partition and you go to Partition in the top, then Swapoff. What happens then ? Can you then delete it ?

---

### Post by msto on 2010-01-31
> **linuxopjemac said:**
> If you select that swap partition and you go to Partition in the top, then Swapoff. What happens then ? Can you then delete it ?

That worked perfectly. :D I deleted the Linux partitions then went back to OS X and used Disk Utility to resize the Mac partition. Thanks a lot!

---

