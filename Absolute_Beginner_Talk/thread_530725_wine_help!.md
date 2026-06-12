---
title: "wine help!"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-08-20
when i uninstall wine, the .wine file is still there. how do i get rid of that? thanks in advance.:)

---

### Post by g2g591 on 2007-08-20
you can just delete it like any other file, but if you wanted it removed when you uninstalled wine, you should have used purge in synaptic instead of remove

---

### Post by axemurder785 on 2007-08-20
i can't delete it like any other file though because when i move it to the trash and then try to delete it from the trash it says: "/home/sam/...t/Desktop" cannot be deleted because you do not have permissions to modify its parent folder.

---

### Post by nitro_n2o on 2007-08-20
> **g2g591 said:**
> you can just delete it like any other file, but if you wanted it removed when you uninstalled wine, you should have used purge in synaptic instead of remove
yeah that's true.. 
you should do
```
sudo aptitude purge wine
```

---

### Post by axemurder785 on 2007-08-20
nvm, i just pressed delete instead of moving to trash and it worked fine. lol

---

