---
title: "Permissions"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Nibiruet on 2006-06-15
Is there a comand I can use to re-set the file permissions as well as folder permissions for all the folders and files under my "My Files" data folder in one swoop instead of tediously having to do so file by file/folder by folder?**[B]**[/B]

---

### Post by taurus on 2006-06-15
```

chmod -R 755 ~/"My Files"

```

---

### Post by Kilz on 2006-06-15
[QUOTE=Nibiruet]Is there a comand I can use to re-set the file permissions as well as folder permissions for all the folders and files under my "My Files" data folder in one swoop instead of tediously having to do so file by file/folder by folder?[/QUOTE]
Yes if you are using [chown]("http://www.ss64.com/bash/chown.html") commands add the -R for recursive.

---

### Post by Nibiruet on 2006-06-15
Thanks!

---

### Post by Nibiruet on 2006-06-15
Thanks ....Worked just great!

---

### Post by Arndt on 2006-06-15
[QUOTE=taurus]```

chmod -R 755 ~/"My Files"

```[/QUOTE]

Note that this adds search permission to all folders, and execute permissions to all regular files. Maybe the latter will turn out to be confusing in some context - it doesn't hurt, though.

---

