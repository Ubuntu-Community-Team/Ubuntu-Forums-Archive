---
title: "Search for file/directories that belong to a specific group"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-06-08
Hello, from the command-line, how can I search for all the file in my whole filesystem that belong to a specific group?

Thank yoU!!

---

### Post by Arndt on 2007-06-08
> **dupa said:**
> Hello, from the command-line, how can I search for all the file in my whole filesystem that belong to a specific group?

Thank yoU!!

Like this, for example:

```
find / -group daemon
```

---

### Post by dupa on 2007-06-08
> **Arndt said:**
> Like this, for example:

```
find / -group daemon
```

thanks!

---

