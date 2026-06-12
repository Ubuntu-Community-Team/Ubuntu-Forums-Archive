---
title: "Help with fstab please"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-06-13
Hi Guys,

How do I change the following terminal command (which works fine) so that it works when included in /etc/fstab/ ?

Thanks.

```
mount -t cifs -o user=<username>,password=<password> //192.168.1.51/<sharename> /mnt/share/
```

---

### Post by Catsworth on 2007-06-13
Also, any files I create (using nautilus) within this folder automatically belong to root, even though I'm logged in as a standard user.

Any way I can change the ownership etc so that I have full control when logged in as me?

Thanks.

---

### Post by Catsworth on 2007-06-13
The correct syntax was:

```
//192.168.1.51/<share> /mnt/<directory> cifs username=<username>,password=<password>,auto,uid=Catsworth,gid=users 0 0

```

---

