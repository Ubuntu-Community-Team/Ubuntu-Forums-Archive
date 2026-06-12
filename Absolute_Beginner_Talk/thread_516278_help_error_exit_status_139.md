---
title: "help error exit status 139"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by catch2two on 2007-08-03
Help my comp was working awesome but now i have this little issue:

i installed a contact thing from add and remove and now i get this error in synaptic and add/remove.

This error is from another app stellarium but it is the same issue i get with everything:

E: stellarium: subprocess post-removal script returned error exit status 139

---

### Post by shearn89 on 2007-08-03
try opening a terminal, and do:
```
sudo apt-get update
sudo apt-get remove stellarium

```

---

