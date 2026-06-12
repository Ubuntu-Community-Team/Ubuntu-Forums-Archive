---
title: "samba question"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2007-04-30
hi I need help sharing files

ubuntu users can access my shared files but when a windows user tries to access my folder it asks for a user name and password.how do I set up username and password so they can access my folders

---

### Post by Najand on 2007-04-30
```

$ sudo smbpasswd -a USERNAME

```
and add password.
Then restart samba using:
```

$ sudo /etc/init.d/samba restart

```

---

### Post by jonathan21 on 2007-04-30
thanks for the help it worked much appreciated

---

