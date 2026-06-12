---
title: "ftp connection error"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-08-30
I installed vsftpd. Everything went ok.
I get this problem when I try to connect to the server with an anonymous account. 

> 
grim@ubuntu:/$ ftp 192.168.1.47
Connected to 192.168.1.47.
220 (vsFTPd 2.0.4)
Name (192.168.1.47:grim): ftp
331 Please specify the password.
Password:
500 OOPS: vsftpd: refusing to run with writable anonymous root
Login failed.
421 Service not available, remote server has closed connection

I have not changed anything in the vsftpd.conf file. I installed vsftpd using :
> sudo aptitude install vsftpd

Does anyone know how to fix my problem. Thank you.

---

### Post by Bachstelze on 2006-08-30
You defined a root directory for the anon account which is writeable, you should CHMOD it to 644 for example.

---

### Post by grim918 on 2006-08-30
I never defined a directory. I just used the defaults. Do you know where the default directory is located.

---

