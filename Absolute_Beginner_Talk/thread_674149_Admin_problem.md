---
title: "Admin problem"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by thom flora on 2008-01-21
When trying to manually run Update Manager, I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I then open a Terminal window and type in dpkg --configure -a, I get THIS error message:

dpkg: requested operation requires superuser privilege

I'm the only user on this system so what does it mean to be a "superuser" and how can I become one?

Thanks for any help.

---

### Post by philinux on 2008-01-21
Type this

sudo dpkg --configure -a

---

### Post by ikex on 2008-01-21
type sudo before the command (then use the password you used to log in)

or to remain root try 
```

sudo bash

```

---

### Post by aysiu on 2008-01-21
**Step 1**
Close Update Manager

**Step 2**
Open a [terminal](http://www.psychocats.net/ubuntu/terminal)

**Step 3**
Paste in this command: ```
sudo dpkg --configure -a
```

---

