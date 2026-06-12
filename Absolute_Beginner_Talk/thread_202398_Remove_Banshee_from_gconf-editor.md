---
title: "Remove Banshee from gconf-editor"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by someusernoob on 2006-06-23
I installed Banshee with synaptic, used it for a while, and did a complete removal the other day. But when i open gconf-editor there is still an entry + dirs of Banshee. How do i get rid of that?

---

### Post by aysiu on 2006-06-23
Try ```
sudo updatedb
locate banshee
grep -inr banshee ~/.gconf
grep -inr banshee ~/.gconfd
```

---

### Post by sancho panza on 2007-10-25
*sudo updatedb* did not help. I removed all the gconf files of the removed apps, and even the locate tool does not show up any folders/settings files. But still, gconf keeps showing all those apps.

---

