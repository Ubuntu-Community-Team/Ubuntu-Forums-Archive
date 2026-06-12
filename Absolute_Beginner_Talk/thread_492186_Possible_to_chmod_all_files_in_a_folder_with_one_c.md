---
title: "Possible to chmod all files in a folder with one command?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-07-04
I know you can change the permissions on a folder using chmod, but can I do it so that it affects all files in the folder and all sub folders?

---

### Post by eternalsword on 2007-07-04
chmod -R xxxx /path/to/top/directory

keep in mind you will still need write permissions on subdirecturies and files for it to take effect on them

---

### Post by Jhorra on 2007-07-04
How about changing the owner?  When I try:

chown -r nobody:nobody /path

It tells me invalid option --r

---

### Post by Jhorra on 2007-07-04
I figured it out, it looks like you have to use a capital r.

---

### Post by eternalsword on 2007-07-04
yep, for recursive using chown, chgrp, chmod you must use capital r.  with chmod, -r lowercase would be removing read permissions hence the capital r and to keep it consistent on these programs they all use the capital r for recursion.

---

