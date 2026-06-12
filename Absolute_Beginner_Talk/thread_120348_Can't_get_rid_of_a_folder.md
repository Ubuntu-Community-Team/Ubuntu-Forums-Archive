---
title: "Can't get rid of a folder"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by johnkennethhughes on 2006-01-21
I have managed to create a folder in my home directory that I now cannot delete. When I try to delete it, a window pops up saying "Error while moving. Cannot move to the wastebasket because you do not have permissions to change it or its parent folder."

Seeing as you can't log on as a root user, how can I get rid of it?

---

### Post by adwait on 2006-01-21
Change its permissions to give you write permissions with
```
chmod +w <dir name
```

Now delete it.

---

### Post by ubuntuuser on 2006-01-21
Or type ```
sudo rm name_here
``` and enter your password when asked. If that folder is not empty type ```
sudo rm -R name_here
``` instead.

---

