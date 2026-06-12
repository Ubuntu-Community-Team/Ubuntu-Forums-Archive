---
title: "Need to Repartition my hdd"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Nymphilis on 2008-02-02
alrighty, well ive intalled ubuntu on my e-drive(not my c drive) and it partitioned correctly, but the problem is, i think i gave too much space to one side, being as i had around 72gb left on a 100gb hdd, and no it has partitioned my drive to 54gb and i had around 2gb free...it cut my hdd to half its size

what im asking is there a way to resieze my partition and give ubuntu like around a 4-5gb partition to work with? plz answer quickly i miss all my hdd space!

---

### Post by Rocket2DMn on 2008-02-02
Boot from the LiveCD and resize with Gparted: System->Administration->Partition Editor

---

### Post by mmb1 on 2008-02-02
Rocket is right, using gparted should be painless, just be sure to resize your ubuntu partition, and not delete anything.

---

### Post by wwbkmd on 2008-02-02
Is the Partition Editor only available on the LiveCD? i.e. You can only change the partition with the LiveCD, correct? Just making sure. Additionally, if you have a virtualBox hard drive, should you leave more than enough space for this? Thanks for the help.

---

### Post by Rocket2DMn on 2008-02-02
> **wwbkmd said:**
> Is the Partition Editor only available on the LiveCD? i.e. You can only change the partition with the LiveCD, correct? Just making sure. Additionally, if you have a virtualBox hard drive, should you leave more than enough space for this? Thanks for the help.

Since it is attached to your root filesystem, you can't fiddle with resizing it.  You can't resize drives that are mounted, so using the LiveCD allows you to modify the drive and partitions that are bordering it.  You CAN download gparted from the repos though, it is nice to have when fiddling with other drives.

---

