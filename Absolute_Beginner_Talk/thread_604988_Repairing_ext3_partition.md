---
title: "Repairing ext3 partition"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Misrule on 2007-11-06
After messing about with various partitions in windows including the ubuntu one (whoops big mistake) I tried to load up with GRUB and now get an error message when I try to load the linux partition it's ext3 so  what should I use to repair it as it only suggests ways of repairing ext2 not ext3. I think there is a problem with the journaling file system, should I just use fschk?

---

### Post by dwblas on 2007-11-06
It depends on what is wrong, but try e2fsck first.  'man e2fsck' will give all of the command line options.  You can use 'mke2fs -j' to format, but then you would loose everything.  If all else fails, reinstall.  It only takes 15-30 minutes, which is better than mucking around for days.

---

### Post by nick_h on 2007-11-06
What is the error message you get?

fsck would be a good starting point.

---

