---
title: "a prob with sudo"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by larvar on 2006-10-07
just finish installing ubuntu 6.06 on my new laptop (thinkpad z60m), and everything seems to be ok. Then I tried:

[B]oem@UbuntuLaptop:~$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
oem@UbuntuLaptop:~$ gksudo gedit /etc/apt/sources.list

(gedit:10919): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]

I cant do sudo! Even as oem-user! I tried other sudo, no :~# just :~$

I really need some help here. Its a clean install. Havent done anything yet. Anyone?

---

### Post by Abstract on 2006-10-07
I think that is an error with Gnome, not gksudo.

---

### Post by taurus on 2006-10-07
Looks like you use alternate CD to install Dapper.  After the first time you boot up, run oem-prepare-configure at the prompt (as it says on the installing screen, if you bother to read it carefully!!!) to create a regular user so you can log in.  That user will be automatically added to groups adm & admin in /etc/group so you can run sudo or gksudo...  Don't use oem to run sudo!

---

### Post by louieb on 2006-10-07
Yes it is very strange. I don't know what the solution is. However the the GKsudo warnning message is normal. I tried the commands in a teminal window and the file was copied. Then gedit loaded and opened the file.
```
lou@gameu:~$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
lou@gameu:~$ gksudo gedit /etc/apt/sources.list

(gedit:7447): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by jordanmthomas on 2006-10-07
This is a known bug by the Gnome developers.  It is marked as low priority...since everything still works.

---

### Post by larvar on 2006-10-07
ok, thanks people. But I did do this when loged in with my regular useraccout, and the same shit happens. but u say that this is a minor prob, and it will not cause any trouble?

---

### Post by jordanmthomas on 2006-10-07
It is not a problem at all.  It is just an annoying error that doesn't really mean anything.  All will still work.

---

### Post by taurus on 2006-10-07
It IS not an error message.  It is a warning...  :rolleyes:

---

