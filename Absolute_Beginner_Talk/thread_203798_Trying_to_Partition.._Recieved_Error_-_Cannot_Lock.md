---
title: "Trying to Partition.. Recieved Error - Cannot Lock Drive."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by virtuexru on 2006-06-25
Using PartitionMagic 8.0. I try to resize my main Windows NFTS Drive and I'm getting a "Cannot Lock Drive" error.

Any help?

---

### Post by hajk on 2006-06-26
May be some other programme is using the disk. Have you tried shutting down and restarting WinXP?

---

### Post by virtuexru on 2006-06-26
[QUOTE=hajk]May be some other programme is using the disk. Have you tried shutting down and restarting WinXP?[/QUOTE]

I said screw it and just formatted. Now I have Windows 2000 PRO and Unbuntu Dual Booted.

---

### Post by hajk on 2006-06-26
You must like Russian Roulette... glad it worked for you.

---

### Post by Brunellus on 2006-06-26
you can't repartition mounted filesystems.

---

### Post by hajk on 2006-06-26
[QUOTE=Brunellus]you can't repartition mounted filesystems.[/QUOTE]

True when partitioning in Linux, but he  was trying to repartition with Partitionmagic, a Windows programme: that's why it is necessary to first shut down anty other programme that could have a read/write lock on the disk.

---

