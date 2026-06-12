---
title: "cant access sharing settings in kubuntu"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by NiksaVel on 2006-08-18
Hey all,

I recently switched from ubuntu to kubuntu to try out what KDE feels like...  so far everything went smoothly except for one problem:

when I click the System settings-sharing-file sharing and click on administrator and enter the password, all the options appear, but are STILL GRAYED OUT and I can't configure the sharing on the computer.


anyone know why this might happen/what to do about it?


thank you very much in advance!:confused:

---

### Post by TooDamFast on 2006-08-18
you must install and set up samba, then you can access those settings. I dont know much about samba but there are some great how tos on the forums.

---

### Post by PriceChild on 2006-08-18
to install samba:
```
sudo apt-get install samba
```
Personally i edit /etc/samba/smb.conf manually to change my settings. then restart samba when finished.

---

### Post by NiksaVel on 2006-08-18
I'll check it, but I'm not sure that's the issue, because I can share files with windows shares on other computers with the default settings...   so samba is probably already installed...

I know I can do it manually and I will if I'll have to... :sad:

---

