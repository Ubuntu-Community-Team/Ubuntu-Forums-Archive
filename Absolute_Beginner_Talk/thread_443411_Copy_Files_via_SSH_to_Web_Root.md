---
title: "Copy Files via SSH to Web Root"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Streamweaver on 2007-05-14
I installed SSH on my 7.04 LAMP server and use it to transfer files but I can't copy them directly to my Web Root folder. What is the best practice for setting this up?

---

### Post by rich.bradshaw on 2007-05-14
Why not? What do you mean?

Is it because /var/root is owned by root?

---

### Post by Streamweaver on 2007-05-14
Sorry, no.  The webroot is /var/www/html and owned by www-data

I can't find a www-data group or user in the user admin and when I try to login under a normal user it wont let me copy the files to that folder.

---

