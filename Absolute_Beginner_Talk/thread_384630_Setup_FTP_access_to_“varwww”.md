---
title: "Setup FTP access to “/var/www/”"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-03-14
I have tried many different ftp servers and I cant seem to get any of them to allow me to change the home directory from “/home/” to “/var/www” 

Is it possible to do that?

---

### Post by Bachstelze on 2007-03-14
Yes, but definitely not a good idea. Why don't you just make a symlink to it ?

```
cd && ln -s /var/www
```

---

### Post by LoicNyssen on 2007-03-14
ummm ok, well if its not such a good idea, whats another way to access my files in that dectory remotly? so that i can upload downlaod etc etc...

---

### Post by annda on 2007-03-14
if you can't/don't want to use symlinks, you can use a safe and secure option: ssh instead of ftp.

here's an idea how it might work:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

---

### Post by LoicNyssen on 2007-03-14
Use ssh to upload and downlaod files? 

I didnt know that was posible... 

How is that done?

---

### Post by oneofth3m on 2007-03-14
If you want to change the directory to /var/www/ you have to comment the following line in /etc/vsftpd.conf
-  chroot_local_user=YES (either comment or set it to NO)

But if your abjective is to enable uploads and downloads you could follow these steps.

Create a new user for ftp:
$ adduser ftpUser

Set a password to this user
 
$ passwd ftpUser

Now open /etc/vsftpd.conf

disable anonymous access (so that anonymous users cant write)

- anonymous_enable=NO

enable write access

- write_enable=YES

set chroot_local_user=YES (so that ftpUser can only create files in /home/ftpUser)

If you want more than one user to have write access its better you create that many accounts.

---

### Post by LoicNyssen on 2007-03-14
> **oneofth3m said:**
> If you want to change the directory to /var/www/ you have to comment the following line in /etc/vsftpd.conf
-  chroot_local_user=YES (either comment or set it to NO)

But if your abjective is to enable uploads and downloads you could follow these steps.

Create a new user for ftp:
$ adduser ftpUser

Set a password to this user
 
$ passwd ftpUser

Now open /etc/vsftpd.conf

disable anonymous access (so that anonymous users cant write)

- anonymous_enable=NO

enable write access

- write_enable=YES

set chroot_local_user=YES (so that ftpUser can only create files in /home/ftpUser)

If you want more than one user to have write access its better you create that many accounts.

i would also need a ftp server app like pure-ftp?

---

### Post by Tipo on 2007-03-14
There is a good article here about general use of SSH (including transferring files!)

[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

:)

---

