---
title: "ddrescue; hdd died during trimiming"
date: 2017-11-17
forum: Any Other OS
---

### Post by Vitrag_Mehta on 2017-11-17
My Vmware esx hdd went bad.


while running ddrescue from a live CD; it was able to generate a 4tb img file; however during the trimming stage the hdd died completely. i am now at a stage where using losetup i am able to mount the img file and see the file and folders. unfortunately the important data files are 0 filled.


the ddrescueview shows the following status
input size 3.99 TB
rescued 876.05GB
non tried 0b
error count 281010
bad sectors 143.8 MB
non-trimmed 1.81 TB
pending 3.12 TB
current pos 2.68 TB
non scraped 1.31 tb


is there any way the data can be recovered from the img file; probably by making sure the non trimmed data is also made visible (not sure; thinking out of desperation).


any help, suggestion on this will really help


the old hdd is now completely out and doesnt even spin up when connected to power.

---

### Post by Vitrag_Mehta on 2017-11-22
any suggestions on how to proceed; please let me know if any further information is required

---

