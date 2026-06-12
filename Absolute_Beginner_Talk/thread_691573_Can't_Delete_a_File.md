---
title: "Can't Delete a File"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by mcy782 on 2008-02-08
I moved a folder from my storage drive to the trash, but it won't delete from trash. It says:

"Error while deleting. /media/disk/.../Folder.jpg" cannot be deleted because you do not have permissions to modify its parent folder."

How do I change the permissions so that I can get rid of the folder? Any help would be appreciated. Thanks

---

### Post by taurus on 2008-02-08
Run this command from a terminal

```
gksudo nautilus
```
and see if you can delete that file with it.

---

### Post by mcy782 on 2008-02-09
That didn't work. Do you know where the trash folder is located within the file system?

---

### Post by mcy782 on 2008-02-09
I stand corrected. It's gone! Thanks all.

---

