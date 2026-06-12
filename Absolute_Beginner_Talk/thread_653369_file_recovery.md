---
title: "file recovery"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2007-12-29
i accidentally deleted my songs which are in windows ntfs partition which occupied some 1.2gb using DELETE.but the free space after deletion is same as the space before deletion.
when i pressed DELETE it didn't ask for any confirmation,but i ve enabled ask for confirmation in properties dialog box.
is there a way 2 recover my free space?
when i press DELETE where will the files will be.are they permanently deleted .i ve checked in trash but no use.
pls do help me...

---

### Post by taurus on 2007-12-29
Look in

Applications -> Accessories -> Terminal
```
ls -la ~/.Trash
df -h ~/.Trash
```

---

