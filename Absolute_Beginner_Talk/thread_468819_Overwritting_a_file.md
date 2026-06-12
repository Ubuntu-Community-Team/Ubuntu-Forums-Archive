---
title: "Overwritting a file"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Red Mystery on 2007-06-09
To install parallels on my computer i need to overwrite one file with another one.  The file that i want to replace the other file with has the permission set as root and i cannot overwrite it.  Is there a way to change the permission of a folder in the terminal?

---

### Post by bodhi.zazen on 2007-06-09
> **Red Mystery said:**
> To install parallels on my computer i need to overwrite one file with another one.  The file that i want to replace the other file with has the permission set as root and i cannot overwrite it.  Is there a way to change the permission of a folder in the terminal?

You do not (and should not) change the permissions. Rather use sudo :

```
sudo cp <file_to_copy> <file_to_copy_to>
```

Replacing with the path of course.

Or if you prefer a gui :

```
gksudo nautilus
```

He he he... try not to abuse these powers.

---

