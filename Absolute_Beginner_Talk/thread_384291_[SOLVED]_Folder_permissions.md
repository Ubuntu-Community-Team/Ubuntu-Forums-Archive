---
title: "[SOLVED] Folder permissions"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-14
Ok so i was just wondering if i change the folder permissions for /var/www/phpmyadmin so that only i can access it, will that stop mysql from working properly? databases, users ect.. or will phpmyadmin automatically protect itself via asking for a username and password?

Thanks, Davey

---

### Post by DaveyG on 2007-03-14
Bump

---

### Post by indytim on 2007-03-14
I took a little bit different approach and assigned my id as the owner on /var/www (and all child folders).

Been running with that config on several different builds of LAMP (dev only - no outside services).

If you're running it in an open environment (Apache opened to the world), then suggest tying down phpMyAdmin with permissions and also enable the password feature for access to phpMyAdmin.

Hope this helps,

IndyTim

---

