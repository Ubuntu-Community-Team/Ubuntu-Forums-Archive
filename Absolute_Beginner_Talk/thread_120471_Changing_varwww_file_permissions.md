---
title: "Changing /var/www file permissions"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by jscrilla on 2006-01-21
Ok, so I thought I knew what I was doing. I changed the file permissions to what I thought were read, write, view that kind of thing, so anyone could view my index.html page. However, now I can't even do a simple ls command. I get permission denied. How to I change the permissions on this file to be all users and what should the proper code be to get it right for web viewing. Thanks! :)

---

### Post by rensu on 2006-01-21
Go to /var folder and try there ls -la and paste here the report.
Actually if you want to fix that stuff then chmod 755 /var/www should fix that problem.

---

### Post by jscrilla on 2006-01-21
[QUOTE=rensu]Go to /var folder and try there ls -la and paste here the report.
Actually if you want to fix that stuff then chmod 755 /var/www should fix that problem.[/QUOTE]

Thanks! That fixed it!

---

