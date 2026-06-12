---
title: "I have a question about ubuntu"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by xtn5021 on 2007-08-14
I was wondering,when you install ubuntu,does it let you make a partition yourself?Or do I have to manually do a partition using windows?

                                                                                                   thanks in advance,
                                                                                                                             Erick

---

### Post by 5-HT on 2007-08-14
Hi,
The installer does include a partition utility.
cheers,

---

### Post by xtn5021 on 2007-08-14
> **5-HT said:**
> Hi,
The installer does include a partition utility.
cheers,thanks mate :) helped me out lots :)

---

### Post by proalan on 2007-08-14
you can do it either way, though there isn't any partitioning tools on xp unless you use something like partition magic.

The ubuntu live cd will provide you with options before installation

- auto partition by using free space on your windows partition (keeps your xp installation but resizes it)
- remove all partitions (will destroy existing partitions including your xp installation)
- manual partition (best option if you know exactly what partitions you want)

If your not familiar with the terms ext3, swap then the auto partitioning by resizing the windows partition is the way to go.

Alternatively you could try WUBI, an executable file which will install ubuntu onto your windows partition without the fear of messing up your harddrive partitions in anyway. And it will allow you to remove ubuntu completely through the add/remove programs utility in windows.

---

### Post by steve.horsley on 2007-08-14
Do not make partitons for Ubuntu with Partition Magic. This seems to cause problems sometimes. It's best to use a Linux based partitioning tool, like the gparted live CD or the Ubuntu installer.

Remember that Linux wants at least 2 partitions. One for the system (usually ext3) and a swap partiton for using as virtual memory.

---

