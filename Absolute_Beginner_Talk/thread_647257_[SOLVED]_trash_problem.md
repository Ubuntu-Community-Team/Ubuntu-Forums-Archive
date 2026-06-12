---
title: "[SOLVED] trash problem"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by rob1984 on 2007-12-22
i got one file in my trash can that won't go away,

"cannot be deleted because you do not have permissions to modify it's parent directory"

is there a command line "empty trash" function that i can sudo?

---

### Post by wormser on 2007-12-22
You could use nautilus with root to delete the file.  Be careful with it.  The trash is a hidden folder so you will need to press Ctrl + h to view hidden files.

```
gksudo nautilus
```

---

### Post by barbedsaber on 2007-12-22
If it works, can you please mark the the thread as solved, you can do this by clicking on thread tools, and then go down to mark thread as solved.

---

### Post by SOULRiDER on 2007-12-22
You could also do:
```
sudo rm -r ~/.Trash
```
which will be easier.

---

### Post by rob1984 on 2007-12-22
thanks!

```
gksudo nautilus
```

worked perfectly!

---

