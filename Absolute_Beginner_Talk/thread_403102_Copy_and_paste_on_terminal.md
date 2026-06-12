---
title: "Copy and paste on terminal"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by mystically on 2007-04-06
I'm tring to install ubuntu looks engine. It requirs me to copy and paste two files that only root can access. How do I copy and paste?

---

### Post by userundefine on 2007-04-06
If you really want to copy and paste, and not cut, you can go
```
sudo cp /path/of/original/file /path/where/you/want/to/paste
```
If you want to cut and paste, substitute **mv** for **cp**.

---

### Post by invalid on 2007-04-06
> **mystically said:**
> I'm tring to install ubuntu looks engine. It requirs me to copy and paste two files that only root can access. How do I copy and paste?

```
sudo cp orig-file copied-file
```

---

### Post by aysiu on 2007-04-06
You don't need the terminal. You can do a simple drag-and-drop. Read this for more details:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

