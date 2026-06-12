---
title: "remove XP"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ronb94 on 2007-12-26
hello i want to totally remove xp from the computer and add the all space this to linux ubuntu/
how to do this?
thank you

---

### Post by Cypher on 2007-12-26
Do you already have Ubuntu installed? If so, you will first need to figure out which partition WinXP is mounted on.

Type
```

sudo fdisk -l

```
to get a list of all the partitions on your machine, once you figure out which is a NTFS partition, you can
```

sudo mke2fs -j <partition name>

```
You should now have a newly formatted EXT3 partition where XP once resided, you can now mount this new partition by adding an entry to the "/etc/fstab" file.
```

man fstab

```
will give you the details of what the options mean..

---

### Post by Crumpets and Jam on 2007-12-26
Re-installing Ubuntu from the Live CD or the Alternative Installation CD and selecting "Use Entire Drive" will write over Windows XP and your current Ubuntu installation leaving you with a fresh intall of Ubuntu Linux. If removing both installations is not an option, follow Cyper's instructions above.

---

### Post by Cypher on 2007-12-26
> **Crumpets and Jam said:**
> Re-installing Ubuntu from the Live CD or the Alternative Installation CD and selecting "Use Entire Drive" will write over Windows XP and your current Ubuntu installation leaving you with a fresh intall of Ubuntu Linux. If removing both installations is not an option, follow Cyper's instructions above.
This would also summarily destroy the /home partition that might contain all your documents. And since the OP wishes to reclaim the storage space from XP, I'm thinking that they have documents in Linux that they don't wish to lose..

---

### Post by omegamike3 on 2007-12-26
> **Cypher said:**
> This would also summarily destroy the /home partition that might contain all your documents. And since the OP wishes to reclaim the storage space from XP, I'm thinking that they have documents in Linux that they don't wish to lose..

Indeed, I would think this is can be assumed. And if that's the case, you can always use gparted to wipe out the XP partition and then resize your current Ubuntu partition to take up the space, so you don't have a separate partition that's left over, meaning, everything is just one big happy drive again. As with doing any sort of partition work, it's always a good idea to back up anything of importance to you, including data from the Ubuntu partition, as things can go wrong and bad clicks can be made. :)

---

### Post by ronb94 on 2007-12-26
ihave ubuntu installed i want to add the free space to the et3 partition

---

