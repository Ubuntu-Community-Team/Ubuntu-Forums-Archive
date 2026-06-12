---
title: "Using Apache locally: Can't open anything!"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by ThinkBuntu on 2007-08-16
I'm trying to test some PHP locally (to avoid the circuitous process of uploading and testing), but for some reason I can't load any files because of a permissions issue.

I changed Apache's default from /var/www to ~/Websites, and the server can't read any of my files. I get load errors on PHP pages, and this error on HTML pages:

> You don't have permission to access /Natural Mystics/directions.htm on this server.

How do I fix this? I fiddled with permissions, making sure to allow "Others" to "Access Files" for all enclosed files, but still no luck.

---

### Post by Rocket2DMn on 2007-08-16
Have you tried:
```
chmod -R 755 ~/Websites/
```
It has to be available to World, not just other users.

---

### Post by hyper_ch on 2007-08-16
well, apache runs as user www-data and so it that user needs to have permissions for those files... but then I'd rather stick the files in /var/www/

---

### Post by ThinkBuntu on 2007-08-16
> **Rocket2DMn said:**
> Have you tried:
```
chmod -R 755 ~/Websites/
```
It has to be available to World, not just other users.
Thanks!

---

