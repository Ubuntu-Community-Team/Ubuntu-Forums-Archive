---
title: "file access..."
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-09-25
So I mounted my windows partition read-only using the ntfs-3g filesystem type.  I copied some files to an ext3 partition but can't access them.  the sudo chown. chmod and chgrp commands don't work.  I also can't delete the directories that were created on the ext3 partition.  I can reformat the partition if I have to but don't want to do that.  There are files elsewhere that need to get moved eventually to some home directories and I want to figure this out.

---

### Post by crokett on 2006-09-25
Never mind.  sudo was not working but an su to root did work

---

