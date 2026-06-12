---
title: "FTP and Read-Only ?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-09-24
Hi,

I have Ubuntu Desktop on one machine and Ubuntu Server on another; have the FTP server running (vsftpd) successfully (user login and write-enabled).

However, I notice that when I am on my Unbuntu Desktop, and connect to the the FTP server to open a file (in gedit or vim) the file opens as read-only.  (I am prompted for a password, which I promptly enter.)  

Also, I cannot move files between directories ... I can add files and delete them, but not move them around or open them to edit them (without saving to desktop first).

This doesn't happen only on my Ubuntu Server running the FTP host, but also remote hosts I use as well.

On my Mac, I use CyberDuck for FTP; with CyberDuck I can open and edit a file as well as move files between directories without a problem (the things Ubuntu won't let me do).  I see to use the same commands to log on (IP addres, username, password).  However: one lets me do more than the other.

Know how to fix this ?  I have tried gftp and that doesn't solve the problem either.

Thanks,
Damon

---

### Post by wieman01 on 2006-09-25
I think this has nothing to do with the FTP server but the folders' access permissions. To change permissions & ownership you have 3 commands available:

1. chmod
2. chown
3. chgrp

Check it out on the forum or via 'man' pages.

---

