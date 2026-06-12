---
title: "Changing the owner of a folder"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by lilalfyalien on 2006-11-04
Hi,

I have the folder /var/www it is currently owned by root. I want to change this so that it's owned by the group ftp. How do I do this (I already have the group waiting!)?

Thanks,


Amy

---

### Post by quux on 2006-11-04
"chgrp" is your friend... you can find an example at the end of the manpage ("man chgrp")

---

### Post by bsussman on 2006-11-04
> **lilalfyalien said:**
> Hi,

I have the folder /var/www it is currently owned by root. I want to change this so that it's owned by the group ftp. How do I do this (I already have the group waiting!)?

Thanks,


Amy
Before doing this you might want to explain why.

It is unusual and probably undesirable for ftp to own your apache web root.  

It is  more usual for the apache daemon user to own this directory

---

### Post by lilalfyalien on 2006-11-04
ok, but still a folder within there... I know not to do it... I just wanted to know how :D

---

### Post by bsussman on 2006-11-04
ok.... :)

the command for group change is chgrp.  It requires root privs to do, so use sudo to run it.

---

### Post by taurus on 2006-11-04
> **lilalfyalien said:**
> ok, but still a folder within there... I know not to do it... I just wanted to know how :D

```
sudo chgrp -R ftp /var/www
```

---

