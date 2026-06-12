---
title: "&quot;gksudo nautilus&quot; error..."
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by azkehmm on 2006-11-22
Ok, so I figured out how to manage files and stuff as an admin/root/su. But, when I type in the magic command, all i get is this 

```
bjarke83@bjarke83-desktop:~$ gksudo nautilus
(nautilus:8687): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols 
specified are supported and host-based authentication failed.

```

I don't understand what it means. Am I so lucky that someone in here will use a few minutes to translate it for me :) Thanks in advance.

---

### Post by Velotix on 2006-11-22
Sounds like one of two problems:

1) The account you're using doesn't have admin/sudo priviledges, in which case you need to change your account's priviledges - and if that's the only user account on your computer, you're in trouble.

2) gksudo itself is either missing, corrupt or not properly configured; your installation is either corrupt or broken.

Unfortunately, unless it's the first one and you have a spare account with sudo priviledges, I can't help you. :/

---

### Post by CatKiller on 2006-11-22
[https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917)

---

