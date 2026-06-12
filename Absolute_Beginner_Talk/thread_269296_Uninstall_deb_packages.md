---
title: "Uninstall deb packages"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-10-01
How do I uninstall a deb package?

---

### Post by skymt on 2006-10-01
```
sudo dpkg -r packagename
```

---

### Post by Qrk on 2006-10-01
The easiest way is to simply find the package in synaptic and select remove. Even if you didn't install it by apt-get, it will appear in synaptic as an installed package. Of course, if you know the packagename, use  "sudo dpkg -r xxx"

---

