---
title: "when I restart apache2 I get this:"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Kuroda_Shun on 2007-11-26
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80

no listening sockets available, shutting down

Unable to open logs
Please tell me there is an easy fix to this. Or don't.

---

### Post by ephro on 2007-11-27
I think you are trying to restart apache2 as a regular user. Try the following command:
```
sudo /etc/init.d/apache2 start
```ephro

---

