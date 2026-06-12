---
title: "How do I Zip a folder?"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-05
Hi,

Does anybody know how to zip a folder using the Terminal? I want to zip the folder and all folders and files within that folder, so I can send it to a friend.

Thanks

EDIT:

Sorry just found out:

```
zip -r folder folder
```

Where folder is the folder you want to zip.

---

### Post by tonyr on 2006-05-05
```

zip -r <folder-name> <folder-name>
```
creates a <folder-name>.zip file

see **man zip**.

It requires, of course, that you have **zip** installed, but I seem to have
it by default.  Or did I misinterpret your question?

---

### Post by aktiwers on 2006-05-05
Thanks Tonyr :)

---

