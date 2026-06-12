---
title: "l can't see any user!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by alooma on 2006-08-30
there are not any user or group on user setting window 
l see only buttons and a white area on this.
how can i change user settings by using console.

---

### Post by Bachstelze on 2006-08-30
What exactly do you want to change ?

---

### Post by alooma on 2006-08-30
l want to give all privileges my user account

---

### Post by Klaidas on 2006-08-30
That's what root is for. Having every right on your account is not safe.
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by Bachstelze on 2006-08-30
That's what sudo is for... If it's to add sudo privileges to a different account than the one you created during install, edit the groups file :

```
sudo nano /etc/group
```

and add your username at the end of the 'admin' line, like this :

```
admin:x:111:user1**,user2**
```

---

### Post by alooma on 2006-08-30
"111" means only to run programs isnt it?

---

### Post by Bachstelze on 2006-08-30
As a CHMOD value, yes. but here it's the gid of the admin group. If yours is diffrerent, leave it untouched.

---

### Post by alooma on 2006-08-30
ok thank you

---

