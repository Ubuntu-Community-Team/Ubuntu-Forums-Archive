---
title: "URGENT HELP - with Synaptic"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by chewit on 2008-01-19
Hi,

I have a major problem with Synaptic. When I up date the list or install an app using synaptic i get this message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any Ideas???

---

### Post by asmoore82 on 2008-01-19
open a terminal and run the fix it suggested, but don't forget "sudo" for root privilege:
```
sudo dpkg --configure -a
```

---

### Post by chewit on 2008-01-19
Thank you asmoore, huge help. Works now. Didn't know sudo was to do with root.

---

### Post by asmoore82 on 2008-01-19
you're very welcome.

> **chewit said:**
> Thank you asmoore, huge help. Works now. Didn't know sudo was to do with root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

