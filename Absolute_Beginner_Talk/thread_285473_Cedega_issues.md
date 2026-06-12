---
title: "Cedega issues"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by FPStanley on 2006-10-26
I recently uninstalled TransGaming Cedega, however, the folder has been left behind in my applications menu despite trying to remove it through the alacarte menu editor (it won't let me). Has anyone else had a similar problem and know a solution? Thank you!

---

### Post by zaziork on 2006-10-29
> **FPStanley said:**
> I recently uninstalled TransGaming Cedega, however, the folder has been left behind in my applications menu despite trying to remove it through the alacarte menu editor (it won't let me). Has anyone else had a similar problem and know a solution? Thank you!

It's probably a permissions issue. Try removing the directory as root, by going to the terminal and typing:

```
sudo rm -r name-of-directory
```

This will remove the named directory and all subdirectories.

---

