---
title: "Alacarte not saving menu settings."
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Verengan on 2006-12-01
My alacarte is not saving menu changes in my user name, root can change its menu just fine, its only this one user that cannot. I assume its just a permissions problem but for the life of me cannot find what I might need to fix. Anyone have some ideas?

---

### Post by RAOF on 2006-12-01
If you've ever tried to use alacarte as root, this can happen.  The problem is, when alacarte writes the config out, it's now owned by root (because it was run by root).  So, now when you run alacarte as your own user, you can't actually write to the config files - they're owned by root, and you don't have write permissions.

A quick fix is to just re-own everything in your home directory, like so:
```
sudo chown *your_user_name* -R ~
```

Replacing *your_user_name* by your username, obviously :)

---

