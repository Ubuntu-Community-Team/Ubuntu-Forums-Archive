---
title: "Massive CHMOD"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-04-03
I need to CHMOD a massive amount of files. I need to CHMOD a folder and all its subdirectories to 755. How can I accomplish this quickly without doing each one individually? Thanks!

---

### Post by Madpilot on 2006-04-03
Use chmod with the -R flag, which stands for recursive.

"chmod 755 -R /path/to/stuff"

---

### Post by amitroy5 on 2006-04-03
This will CHMOD the directory and all subdirectories and files, right? Thanks!

[QUOTE=Madpilot]Use chmod with the -R flag, which stands for recursive.

"chmod 755 -R /path/to/stuff"[/QUOTE]

---

### Post by xenmax on 2006-04-03
yup, that is what the -R does

---

### Post by jrib on 2006-04-03
that will chmod all the files too.  If you want only directories and subdirectories, you would need to do something like:

```
cd /path/to/directory
```
```
find . -type d -exec chmod 755 '{}' \;
```

---

