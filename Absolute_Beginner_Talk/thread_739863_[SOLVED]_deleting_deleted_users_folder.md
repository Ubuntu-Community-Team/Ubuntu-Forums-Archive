---
title: "[SOLVED] deleting deleted users folder"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by satipera on 2008-03-30
during an attempt to solve another problem i created an additional user which i have now deleted from being able to access the system, but the user folder is still on the system, how do i get rid of it?

---

### Post by Oldsoldier2003 on 2008-03-30
> **satipera said:**
> during an attempt to solve another problem i created an additional user which i have now deleted from being able to access the system, but the user folder is still on the system, how do i get rid of it?
```

sudo rm -r /home/<username>
```

---

### Post by wormser on 2008-03-30
```
cd /home
```
```
sudo rm -R userfolder
```

Just make sure you delete the correct user's folder!

---

