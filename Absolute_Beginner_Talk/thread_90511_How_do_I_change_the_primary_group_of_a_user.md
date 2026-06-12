---
title: "How do I change the primary group of a user?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-15
Using 'usermod -g' command does assign a new primary group to the user, but it also demote the original primary group to be the secondary group.

Is there a command to assign a new primary group to a user without any secondary group?

Thanks !

---

### Post by yoyoned on 2005-11-16
use a uppercase G and then list the groups sererated by comma
 
```
usermod -G users,games,audio youruser 
```

---

