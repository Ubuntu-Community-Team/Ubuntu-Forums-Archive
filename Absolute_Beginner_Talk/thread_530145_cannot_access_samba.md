---
title: "cannot access samba"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by mstrap123 on 2007-08-20
i install samba on a ubuntu 6.10 server, but i cannot view or access server, i can view the workgroup but when i expand it say i dont have permision to it, i try to ping the server but it return "request time out".

---

### Post by ukripper on 2007-08-20
> **mstrap123 said:**
> i install samba on a ubuntu 6.10 server, but i cannot view or access server, i can view the workgroup but when i expand it say i dont have permision to it, i try to ping the server but it return "request time out".

Have you configured your smb.conf according to your network?

```
sudo gedit /etc/samba/smb.conf
```

---

### Post by mstrap123 on 2007-08-20
i have configure the smb.conf to a different workgroup, did it cause that?

---

### Post by ukripper on 2007-08-20
> **mstrap123 said:**
> i have configure the smb.conf to a different workgroup, did it cause that?

if workgroup is different for your network it won't be able to talk to your other machines. it also depends upon what kind of network setup you have. If explain what you trying to achieve from the networking then it would be much easier to help you out with.

---

### Post by mstrap123 on 2007-08-20
i m trying to build a file sharing server using ubuntu & samba for ms window workstation

---

### Post by StooJ on 2007-08-20
Start to finish guide for you:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by ukripper on 2007-08-20
is it internal for file sharing or you want external too? For external you might need to make it either FTP server or webserver for file sharing for internal you just need samba configured and you ready to go.


Follow the guide above as posted it is a very good guide.
Make sure when you change your smb.conf then change
;browseable = no to** browseable = yes** and don't forget to remove ; from front

also do the same for writable = no

---

### Post by dacui on 2007-08-20
Do you create an user has permission to login to samba server?
I think **smbpasswd** command can help you.:)

---

### Post by mstrap123 on 2007-08-20
i change the server to the same workgroup as my workstation, now i can see the server but still cannot access it

---

### Post by ukripper on 2007-08-21
> **ukripper said:**
> 
Make sure when you change your smb.conf then change
;browseable = no to** browseable = yes** and don't forget to remove ; from front

also do the same for writable = no

Follow the steps as mentioned above my me.
[B]browseable = yes
writable = yes[/B]

---

### Post by mstrap123 on 2007-08-21
i already set the** browseable** and **writable** to yes but still cannot access the server

---

### Post by ukripper on 2007-08-22
> **mstrap123 said:**
> i already set the** browseable** and **writable** to yes but still cannot access the server

Are you able to access other machines peer to peer with samba?

---

### Post by mstrap123 on 2007-08-23
no, i cant even ping the samba machine.

---

### Post by ukripper on 2007-08-24
Are you using router, hub or switch?

---

