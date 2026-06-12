---
title: "Backup which partitions?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by davidpbrown on 2007-07-22
I'm thinking I could restore from worst case, if I have a copy of..
- the output from parted print
- /etc/fstab
- sudo dpkg --get-selections > package_list
- a backup of ?partitions

But which of these partitions must be formatted when Ubuntu is reinstalled?.. which is it useful to backup??
/
/home
/root
/tmp
/usr
/usr/local
/var
swap

Is there anything else that might be needed to restore a complete system?

---

### Post by por100pre1 on 2007-07-22
In a bare bones perspective, you SHOULD backup /home . Everything else can be optional.

---

