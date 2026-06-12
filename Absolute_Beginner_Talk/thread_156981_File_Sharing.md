---
title: "File Sharing????"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-04-08
Hi all! I have absolutely no network experience what so ever. I have suceded in sharing the default shared folder of my WinXP machine and can access it from Ubuntu but can not seem to be able to make any other be shared without a password prompt appearing. I wonder what am I supposed to type in the "Authentication Required" dialog box since I don't remember ever creating a network account, and my regular username doesn't seem to work.

please help!! :( 

thanx in advance!

---

### Post by sYs^ on 2006-04-08
Hi!

I'm currently not on linux, but I think U should create a Samba User:

```
smbpasswd -a <user>
```

<user> = username, you can choose it and after pressing enter, it'll ask you for a password.
With this user you will be able to access your samba shares.

I hope it'll help.

---

### Post by belikralj on 2006-04-16
Thanx I'll try that and post right back

---

### Post by nalmeth on 2006-04-16
From windows try blank username and password.
Just hit enter twice.
The key is editing your /etc/samba/smb.conf file to suit your needs. [This page]("http://doc.gwos.org/index.php/Share_files_using_Samba") should give you some good information:

---

