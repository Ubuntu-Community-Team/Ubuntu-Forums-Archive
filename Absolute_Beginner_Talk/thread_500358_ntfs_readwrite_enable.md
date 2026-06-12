---
title: "ntfs read/write enable"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-07-13
looking forward for away to be able reading and writing on windows ntfs partitions from inside ubuntu linux, any idea ??

---

### Post by Vajra Vrtti on 2007-07-13
In Feisty:
[LIST=1]
[*]Install package **ntfs-config**.
[*]Open *System Tools -> NTFS Configuration Tool*.
[*]Enable write support.
[/LIST]

---

### Post by Rocket2DMn on 2007-07-13
You need to get ntfs-3g
```
sudo apt-get install ntfs-3g
```You can then run ntfs-config to set up the write enable.
You may also need to add an entry to your /etc/fstab file so it will automount.

---

### Post by Das Oracle on 2007-07-16
just wanted to say thanks.

---

