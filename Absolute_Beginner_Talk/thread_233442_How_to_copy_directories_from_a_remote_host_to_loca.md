---
title: "How to copy directories from a remote host to local machine with Rsync?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-10
Remote machine : 192.168.1.1 (hostname : testpc)
Remote directory to be copied : Everything under /home
Local directory to copied to : /home

Tried this command

rsync -avz 192.168.1.1:/home/ /home

and 

rsync -avz testpc:/home/ /home

Gives me an error files or directory not found.

Please advise.

Thanks!

---

### Post by melissawm on 2006-08-10
Maybe this is stupid - I don't understand that much about networks - but can't you setup ssh on both machines and do a

```
scp user@remotemachine:/home/* .
```

?

That's how I transfer my files..

---

### Post by starscalling on 2006-11-25
ncftp works great

rsync has ssh option in the manual but ncftp ::
```

ncftp -u user_on_remote_machine -p password_of_said_user ip_of_remote_machine
```

---

