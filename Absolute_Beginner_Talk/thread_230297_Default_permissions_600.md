---
title: "Default permissions 600?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-08-05
When I make a file with the "rt click > create document > empty file" it's permissions are always set to 600. How can I change it to be set to 644 as default?

---

### Post by lamego on 2006-08-05
The default file privileges depend on a environment setting called "umask".
To understand how umask works open a terminal and type "man umask" .
When you get clear on how it works you can change its value on /etc/profile .
You will need to restart the system to make it effective.

---

### Post by Aurdal on 2006-08-05
```
$ man umask
No manual entry for umask
```

There are no manual pages...

---

### Post by taurus on 2006-08-05
At the bottom of ~/.bashrc, add

```

umask=022

```

---

