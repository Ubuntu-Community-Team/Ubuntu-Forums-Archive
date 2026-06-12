---
title: "samba server permissions problem"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by hardipdhillon on 2007-03-19
I have configured samba as a file server.I have make it a domain member in windows environment.I am having problem with permissions the users that i have created in samba and linux are accessing each others shared folder even when i given the valid users option and folder has no rwx to any body other than the owner.,i have user guest ok =yes and witeable =yes

---

### Post by simonn on 2007-03-19
> **hardipdhillon said:**
> i have user guest ok =yes and witeable =yes

You probably do not want this if you want to restrict users to thier home dir - assuming this is what you want to do?

The below is probably more in line with what you want.

```

[global]
...
   security = user
...

[homes]
   comment = Home Directories
   writable = yes
   create mask = 0600
   directory mask = 0700


```

---

### Post by hardipdhillon on 2007-03-19
but i don't want that every time it will ask for password that's why i have given security=share,

---

### Post by simonn on 2007-03-19
post your smb.conf

---

