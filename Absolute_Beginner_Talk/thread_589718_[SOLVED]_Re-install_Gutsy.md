---
title: "[SOLVED] Re-install Gutsy"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-10-24
How can I install Gutsy without creation a new Partition(s)? Step by step please. I know very little about this.

---

### Post by Dr Small on 2007-10-24
When at partitions, select manual.
Then select the partition that you want to install it on, and it will reinstall the OS over the selected partition, without creating a new one.

Dr Small

---

### Post by ukripper on 2007-10-24
You do need to have atleast **/ **(root) and **SWAP** partitions to run Linux and /home is optional if you wish to include that too but it is highly desirable to have one.

---

### Post by mikewhatever on 2007-10-24
At the partitioning stage, choose the Manual option, identify the partitions intended for Ubuntu (root, swap, home if it is separate), mount these partitions as /, swap and /home correspondingly (right click on each and select the mount point), and lastly, opt to format the root partition. The rest of the installation should be regular.

---

