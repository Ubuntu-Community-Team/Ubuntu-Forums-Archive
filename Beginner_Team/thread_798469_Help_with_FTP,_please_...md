---
title: "Help with FTP, please .."
date: 2008-05-18
forum: Beginner Team
---

### Post by eddie67 on 2008-05-18
Hello. 

I have a 6.06 lamp server (almost) working.

I am now trying to set up FTP on the server.

Vsftpd is installed without warnings, but I can not get access from my FTP-client (Filezilla). Username=OK, after password I get "access denied". 

So I guess it has to do with users. In the vsftpd.conf I setup a ftp-user, but where do I define a password for this user and the permitions?

Would it be better or more easy to change to, say, Proftpd ?

Regards

Eddie.

---

### Post by altonbr on 2008-06-13
System users, which FTP uses, are created by typing 'adduser $username' on the command-line or through "System > Admin > Users and Groups" using the desktop.

If you need more information on 'adduser', type 'man adduser'.

So, to test FTP, trying logging in as yourself from another computer. Then, if that works, try it by creating another user.

---

### Post by holiday on 2008-06-13
Are you trying to enable anonymous access?

[http://beginlinux.com/index.php/server_training/ftp-server/120-ftp-server/987-build-an-ubuntu-ftp-server](http://beginlinux.com/index.php/server_training/ftp-server/120-ftp-server/987-build-an-ubuntu-ftp-server)

I don't do that. I create users for my ftp friends and then create symlinks in their home directory to the directories I want to distribute - ensuring they have group read access to those directories.

This isn't a standard approach, but I'm not an interesting target and these are my friends so .... But it works. 

If you're working for the CIA or something, consult with your IT team.

---

