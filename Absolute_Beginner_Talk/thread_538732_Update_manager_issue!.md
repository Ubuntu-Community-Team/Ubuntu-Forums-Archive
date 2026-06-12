---
title: "Update manager issue!"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by AcademyKP03 on 2007-08-30
Beginner here .... I think when I tried to install sunbird manually, it changed some configuration file ..... and now when i get updates and click to update my computer it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any assistance would greatly be appreciated

John

---

### Post by forestpixie on 2007-08-30
open a terminal ( accessories >terminal)
run this command

```
sudo dpkg --configure -a
```

it'll ask for password - it won't show as you type - that's normal

---

### Post by AcademyKP03 on 2007-08-30
works perfectly!  Thank you!!!!!

---

