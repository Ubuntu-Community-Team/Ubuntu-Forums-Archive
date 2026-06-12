---
title: "Apache 2 Multiple protected folders - how?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-12-16
I have managed to protect a single folder on my apache2 server, but would like to do a couple more with different users/passwords.


I tried adding another entry in my apache2.conf file, but it would not do the second one.

```
<Directory /var/www/protected>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/htpasswd
Require user *******
</Directory>

<Directory /var/www/work>
AuthType Basic
AuthName "Project files"
AuthUserFile /etc/apache2/htpasswd2
Require user *****
</Directory>
```

The above was added to the end of my conf file and the user names have been changed for security. ;) 


Any help would be much appreciated.

---

