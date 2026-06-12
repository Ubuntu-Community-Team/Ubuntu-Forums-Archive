---
title: "Really stupid help please RE: permissions"
date: 2007-08-31
forum: Apple Intel Users
---

### Post by r.youden@mac.com on 2007-08-31
OK, I am really new to this Unix stuff and I need to transfer a folder to the following location /usr/local/bin but I am informed that I don't have sufficient permissions. 

How can I get the files into that folder?

Thanks.

---

### Post by alephsmith on 2007-08-31
use the program sudo. ie prefix any commands with "sudo"

```
sudo cp /your/file/name /your/file/destination
```

---

### Post by ajgreeny on 2007-08-31
Just out of interest, why do you need to put a file there?  That folder is usually for binary files that run programs installed by apt-get, dpkg etc.

---

### Post by r.youden@mac.com on 2007-08-31
I am 'trying' to run an embedded ARM processor on a development board and those are the instructions that I have been given so I am just doing as I am told!

Thanks for the advice.

---

