---
title: "Still won't connect to Vista"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by bowler802 on 2007-12-24
Trying to use connect to server.

username: mike
domain name: (left blank because I'm in workgroup mode(home) is the name tried that to.
password: ****

Tells me I don't have permission

I vista the permissions are \\mike-pc\mike (owner)
__________________

---

### Post by LowSky on 2007-12-24
have you installed Samba?

---

### Post by bowler802 on 2007-12-24
The repository says i have samba common. Just installed unbuntu 2 days ago I don't know what i'm doing yet.

---

### Post by dnvikram on 2007-12-24
If Linux and Windows have to share files with each other,then one needs to install Samba packages.Install Samba Client,Samba common,samba utilities and other relevant packages and required packages.Install those packages and restart the samba services and make sure you have setup the share configuration proprely and it should work now.

---

