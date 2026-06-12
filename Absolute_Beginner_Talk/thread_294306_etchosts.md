---
title: "/etc/hosts"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by in_orbit on 2006-11-06
In order to fix the sudo problem, "unable to lookup * via gethostbyname()", where * is the name of my computer, I did some editing in the file /etc/hosts . I added the following row:

"127.0.0.1 localhost *"

Anyway, this solved the sudo problem but when I later restared the computer and tried to login the system hanged. The system starts correctly if this row is removed. What have I done wrong?

/In orbit

---

### Post by taurus on 2006-11-06
```

127.0.0.1 localhost localhost
# if you call your computer a localhost!!!

```

---

### Post by bsussman on 2006-11-06
Deleted Deleted

---

