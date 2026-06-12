---
title: "permissions questions"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by newtoitall on 2007-07-09
/home/me has most of the permissions. /root has none, is that backward? i didn't change anything did I somehow mess up when I was installing Ubuntu and make myself admin?

---

### Post by Pragmatist on 2007-07-09
Please give more information.  What are the permissions of your home directory?
```
ls -l -d  /home/me
```

How about for your /root directory?
```
ls -l -d /root
```

In both case include the owner and group.  For example:

> drwxr-xr-x 72 me me 4096 2007-07-09 09:49 /home/me


> drwxr-xr-x 18 root root 4096 2007-06-25 07:55 /root

---

### Post by aysiu on 2007-07-09
I don't know what you mean by "most," but that otherwise sounds right to me.

You should have permission to your own home directory but no permission to /root

---

### Post by Omnios on 2007-07-09
Permissions for root is a security layer. You have to use the sudo command as root to mod them. This stops things from accessing your core files unlike windows where everything is open for attack. This may be a pain but makes Ubuntu more secure.

---

### Post by newtoitall on 2007-07-09
thank you, it appears i didn't mess up anything after all from the sounds of it.

drwx------ 47 me me 4096 2007-07-09 11:26 /home/me

drwxr-xr-x 10 root root 4096 2007-06-21 14:14 /root

there are only a few boxes unchecked under /me. Fuse filesystems and send and receive fax

---

