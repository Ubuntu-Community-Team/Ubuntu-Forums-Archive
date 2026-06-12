---
title: "[SOLVED] Where do files go when you delete them as root?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Theo148 on 2008-04-09
I recently used 'gksudo nautilus' to do some work with the files on my system (mainly fiddling around with my Firefox installation in /opt) and I assumed that once you deleted a file while using gksudo, you couldn't get it back (since it didn't appear in the trash directory). But oddly enough when I deleted 2 folders that happened to have the same name, just before the second folder disappeared, '(copy)' appeared on the end of its name as if it hadn't gone forever but had simply been moved to a trash directory of some sort with the other folder.

So where is this directory?

---

### Post by ShodanjoDM on 2008-04-09
If you have logged in from gdm as root before, you can try to look in  /root/.Trash

It's a hidden folder, so you have to enable "Show Hidden Files" in nautilus or just typed this command:

```
ls -hal /root/.Trash
```

---

### Post by Theo148 on 2008-04-09
Ah, thank you - that cleared things up a bit. :)

---

