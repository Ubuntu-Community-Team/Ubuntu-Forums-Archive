---
title: "Partition placement"
date: 2009-04-27
forum: Apple Hardware Users
---

### Post by jtslau on 2009-04-27
Does the boot partition (I have a separate /boot partition) have to be placed before the home partition (also have a separate /home partition), and is there anyway around this if this is actually the case?

Just wondering since I can't seem to boot Ubuntu if I have my partition table in this order:

|EFI| |Apple| |Empty: for EFI| |Windows| |/home| |/boot| |swap| |/|

---

### Post by cyberdork33 on 2009-04-28
the partition you boot from needs to be one of the first 4 partitions.

---

### Post by jtslau on 2009-04-29
Thanks

---

