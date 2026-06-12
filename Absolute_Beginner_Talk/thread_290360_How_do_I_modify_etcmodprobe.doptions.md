---
title: "How do I modify /etc/modprobe.d/options"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2006-11-01
How do I modify the file: /etc/modprobe.d/options

When I open it in Places - Computer it says read only. I don't have permission to modify it.

Thanks

---

### Post by Jussi Kukkonen on 2006-11-01
```
gksudo "gedit /etc/modprobe.d/options"

```
in terminal. That'll open the editor with root privileges.

Make sure you know what you are doing with your new-found powers ;) and remember to take backups of system files you change.

---

### Post by Tweedicus on 2006-11-01
Thanks for that. It works. May the force be with me...

---

