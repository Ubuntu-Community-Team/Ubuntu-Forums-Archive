---
title: "cgi permissions"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Transcend on 2007-08-15
so i can get to the place holder page with apache  but when i attempt to get to the /cgi-bin/ it says i dont have permissions

"You don't have permission to access /cgi-bin/ on this server."

what do i do  to accept incoming request?

---

### Post by Rocket2DMn on 2007-08-15
you need to set the folder and its contents with the proper permissions.  Use 755 since cgi-bin holds executables
```
sudo chmod -R 755 /path/to/apache/cgi-bin
like:
sudo chmod -R 755 /var/www/cgi-bin
```
Then refresh the page.

---

