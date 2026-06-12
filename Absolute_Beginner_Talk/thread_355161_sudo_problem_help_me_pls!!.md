---
title: "sudo problem help me pls!!"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by violin on 2007-02-06
when i do sudo it gives me this error 


[PHP]sudo: must be setuid root[/PHP]


how can i fix that?

[PHP] ls -l /usr/bin/sudo 
-rwxrwxrwx 1 root root 91508 2006-10-09 13:37 /usr/bin/sudo
[/PHP]

---

### Post by nhandler on 2007-02-06
Try this command
```
chmod 4111 /usr/local/bin/sudo
```

---

