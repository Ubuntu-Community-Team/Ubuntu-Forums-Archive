---
title: "permisions or a file"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-08-07
I recently created a folder as root.now i do not have permisions to access it.the folder had been created when converting a tar file to deb.what to know how to change permisions for that folder

---

### Post by davebgimp on 2006-08-07
> **jonathan21 said:**
> I recently created a folder as root.now i do not have permisions to access it.the folder had been created when converting a tar file to deb.what to know how to change permisions for that folder

sudo chown -R 'username' 'folder'

sudo chgroup -R 'username' 'folder'

---

