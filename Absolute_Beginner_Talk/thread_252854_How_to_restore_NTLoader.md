---
title: "How to restore NTLoader?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by geekphreak on 2006-09-07
I have a machine with 2 hard drives and I had XP on one and Linux on the other. I reformatted the Linux drive, but GRUB was written to the Windows drive and now XP will not boot, because GRUB won't work. How can I get NTLoader back? I tried repairing XP installation, but that did not overwrite GRUB. I tried fdisk /mbr, did not work either.
What is a good way of restoring NTLoader?

---

### Post by powder on 2006-09-07
Try loading the recovery console and use the "fixmbr" command.

---

### Post by geekphreak on 2006-09-07
Gosh, how come I had not thought of that? Thanks, will try that next.

---

