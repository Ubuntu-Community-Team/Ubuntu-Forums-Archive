---
title: "authnicating windows users to access samba share"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by hardipdhillon on 2007-03-16
i have ubuntu server configured as file server in windows domain.i have given security=share so that no password will  be asked if any windows user is try to browse samba server.now i have created a share and is given valid user=a,i have created this user in linux and samba given full permissions to rwx.i have also created same user in windows with same password,it can read the share but not able to write.plz help me.

---

### Post by apjone on 2007-03-16
have you added
```

 writable = yes

```

to the smb.conf for the share ?

---

