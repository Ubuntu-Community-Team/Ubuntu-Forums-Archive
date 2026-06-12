---
title: "ext2 or 3?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-08-29
I want to reformat an old hard drive purely for storage of files under 1MB.  Which file system should I use?

---

### Post by bruce89 on 2006-08-29
Ext2 is anchient, so of these 2, it would be ext3.

---

### Post by coffeecat on 2006-08-29
ext3 is simply ext2 with journalling added. That gives you the possibility of recovering data after an unclean shutdown or crash. So choose ext3 for an external hard-drive. **But**, should you want to use a Linux filesystem on an external flash drive instead of fat32, **don't** use ext3. Use ext2. The journalling will cause writes to the same place with each read/write to a file wherever this is in the filesytem and the flash drive will fail very quickly.

---

