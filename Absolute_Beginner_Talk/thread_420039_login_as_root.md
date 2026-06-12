---
title: "login as root"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-04-23
Hi,

I am doing some bluetooth socket programming and looks like I have some problems as I am not logged in as root. I know its not safe but I have to do this as I cannot execute my programs. Can sme one tell me how to login as root in Ubuntu Dapper Drake,

thanks

bluezapper.

---

### Post by simonn on 2007-04-23
Just use:

```

$ sudo -s

```

---

### Post by Skrynesaver on 2007-04-23
```
sudo su -
```
Will give you a root shell
```
passwd 
```
while in this shell will give root a direct login.  surely though you can 
```
sudo <programname>
```

---

### Post by bluezapper on 2007-04-23
Thanks for the replies, but, cant I login as root to my Gnome desktop.

---

### Post by Pobega on 2007-04-23
Use gksu to open specific applications as root; I think on Ubuntu it's gksudo. So:

gksudo <bluetooth app>

And type in your password at the prompt.

---

### Post by bluezapper on 2007-04-23
Thanks a lot, it works now.:)

but

(bluescangui:8410): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

