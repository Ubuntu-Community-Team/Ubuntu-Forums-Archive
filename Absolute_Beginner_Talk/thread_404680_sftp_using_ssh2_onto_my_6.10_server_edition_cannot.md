---
title: "sftp using ssh2 onto my 6.10 server edition cannot delete files"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by ghmercado on 2007-04-08
hi im using filezilla to sftp using ssh2 stuff onto my test ubuntu 6.10 and i cannot seem to delete / add / edit files, generating a 'rmdir (directory) permission denied' when trying to delete.

this requires me to have to login to sudo rmdir to do so.

how can i do this via ftp? i understand the security implications but since this is a test webserver its convenient for me at the moment.

many thanks

---

### Post by Bachstelze on 2007-04-08
You cannot do this via sftp (well, you can if you log in as root but I strongly discourage that).

What I'd do if I were you is logging in via standard SSH, and chown /var/www to you since you don't need to mess with stuff outside it and it is not a very sensible directory security-wise.

---

### Post by ghmercado on 2007-04-08
ah i see i see. thanks so much!

---

