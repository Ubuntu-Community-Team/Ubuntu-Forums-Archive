---
title: "[SOLVED] don't have permission to write to a folder"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by texplorer on 2007-07-31
I want to move a folder called XAMPP to my OPT folder but I got a promote says don't have permission to write to OPT folder. How do gain more rights? I installed ubuntu myself, but I guess I also transfered XP settings to it when I install it, the account from XP is not a Admin account. 

thanks,

---

### Post by wolfen69 on 2007-07-31
root access:
```
gksudo nautilus
```

---

### Post by Ek0nomik on 2007-07-31
```
sudo mv XAMPP /opt/
```

---

### Post by feistyfirsttimer on 2007-07-31
> I installed ubuntu myself, but I guess I also transfered XP settings to it when I install it, the account from XP is not a Admin account.

The account you used on XP won't affect your Ubuntu.  If you installed Ubuntu, the user account you created during installation has admin rights and you can use sudo to run as root, as advised above.

---

### Post by aysiu on 2007-07-31
> **wolfen69 said:**
> root access:
```
gksudo nautilus
```
More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by texplorer on 2007-07-31
Thanks guys, you rock:)

---

