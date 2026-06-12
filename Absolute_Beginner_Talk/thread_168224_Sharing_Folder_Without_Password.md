---
title: "Sharing Folder Without Password"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-04-30
I want to share a folder on my network that is not password protected. I want to create a network attached storage. How can I create such a folder? Thanks!

---

### Post by Nikusan on 2006-04-30
[QUOTE=amitroy5]I want to share a folder on my network that is not password protected. I want to create a network attached storage. How can I create such a folder? Thanks![/QUOTE]

change your /etc/samba/smb.conf to look something like this:
```
[global]
security = share
netbios name = ubuntu

[share_name]
path = /path/to/share
available = yes
browseable = yes
public = yes
guest ok = yes
writable = no

```

---

### Post by amitroy5 on 2006-04-30
Should I change writable = yes to edit the files?

---

### Post by Nikusan on 2006-04-30
[QUOTE=amitroy5]Should I change writable = yes to edit the files?[/QUOTE]

Network attached storage... yep, that's exactly what you should do :D

---

### Post by amitroy5 on 2006-05-04
Thanks for your help. However, I don't want it to prompt for a password.

---

### Post by Nikusan on 2006-05-04
[QUOTE=amitroy5]Thanks for your help. However, I don't want it to prompt for a password.[/QUOTE]

With security set to share and guest ok set to yes it shouldn't prompt for a password. Try restarting samba:
```
sudo /etc/init.d/samba restart
```

---

### Post by amitroy5 on 2006-05-31
I have the following path:

[share_name]
path = /path/to/share
available = yes
browseable = yes
public = yes
guest ok = yes
writable = yes

How do I password protect this directory using my Ubuntu password? Thanks! (the one I have to use whenever I use sudo)

---

