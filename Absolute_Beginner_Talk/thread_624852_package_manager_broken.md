---
title: "package manager broken"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by raggielyle on 2007-11-27
Please would someone help me. I have broken the package manager and I get the following message:
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I have run this command with sudo but there is another message that su is required. Run with su but my password is not accepted. Really want to avoid re-installing.
I guess we beginners must drive the old salts mad!
Thank You

---

### Post by FuturePilot on 2007-11-27
If you run it with sudo there shouldn't be an error message about su
Try
```
sudo dpkg --configure -a
```

---

