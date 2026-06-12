---
title: "HDD problem"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by jmrweb on 2006-08-12
Hi 
i removed fedora from my hdd by using gparted in the live ubuntu cd so that i could install ubuntu
but since then i have been unable to access my hdd 
it keeps coming up in gparted as unallocated and also when loading the live cd it gives an error of i/o buffer error on hdd 0 logical block 0

anybody any ideas how to cure this befdore i lose my comp for 5 to 10 days while it goes back under guarantee.

thank john in sheffield uk

---

### Post by siacs on 2006-08-14
You need to create a new partition again after deleting it. Click on the unallocated space, then create new and choose type ext3, then format it.

---

