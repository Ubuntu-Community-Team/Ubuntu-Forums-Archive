---
title: "ntfs 3g problem"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by cotiK on 2007-05-06
i installed ntfs 3g through automatix. it seems to be working pretty well but when i sent a file to trash from a mounted ntfs drive it disappears (completely deleted) rather than going to trash
Can i change that?

---

### Post by Biochem on 2007-05-06
When you delete a document on a NTFS drive the file is sent to a .trash-username folder on the drive. it is hidden but can be viewed by typing ctrl+h in nautilus. The trash is however not supported in linux and its content need to be deleted manually using Shift+delete "which circumvent the trash and directly delete the file".

---

### Post by Happy_Man on 2007-05-06
It doesn't actually disappear, it goes to a hidden folder named .Trash-<your username>. This is because the trash applet Ubuntu uses can't support NTFS, and ntfs-3g can do nothing to change that.

---

