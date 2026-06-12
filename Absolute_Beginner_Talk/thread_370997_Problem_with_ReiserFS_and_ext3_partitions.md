---
title: "Problem with ReiserFS and ext3 partitions"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by alican timur on 2007-02-26
i had my hard disk partitioned into two pieces, 80 was ext3, the rest was reiserfs. i decided to delete the ext 3 partition and spare everything for the reiserfs, which had the ubuntu installation, so i booted up with the live cd, deleted ext3 partition and resized the reiserfs partition. when i tried to boot up my installation it gave an error while its checking all the filesystems. do i need to modify the fstab file? can someone please help?

---

### Post by taurus on 2007-02-26
If you delete a partition, you need to delete the entry for it from your /etc/fstab as well if you have it in there.

---

### Post by alican timur on 2007-02-26
that solved it thanks ^^

---

