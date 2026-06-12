---
title: "File permissions help"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by aliasbs on 2006-08-05
Im trying to modify a file but cant figure out how to open it in root.  If i open it normally it will be a read only file and i cant make modifications to it.

Im trying to modify /etc/dhcp3/dhclient.conf but i am unable to save the changes because its read only.

---

### Post by user1397 on 2006-08-05
> **aliasbs said:**
> Im trying to modify a file but cant figure out how to open it in root.  If i open it normally it will be a read only file and i cant make modifications to it.

Im trying to modify /etc/dhcp3/dhclient.conf but i am unable to save the changes because its read only.try in a terminal (applications>accessories>terminal): ```
gksudo gedit /etc/dhcp3/dhclient.conf
```

---

### Post by aliasbs on 2006-08-05
Awesome!  That worked for me.

Thank you

---

