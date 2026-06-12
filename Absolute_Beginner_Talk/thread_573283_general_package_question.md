---
title: "general package question"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-10-11
i have noticed, with some packages, that they will bring up some form of GUI config menu. i will use LDAP as an example but ive noticed it with other packages too. so i:
```
apt-get install libpam-ldap libnss-ldap
```

the problem is i messed up the GUI config. I thought, no problem ill just:
```
apt-get remove libpam-ldap libnss-ldap
```
and to make sure its completely gone
```
apt-get --purge remove libpam-ldap libnss-ldap
```

and reinstall, thinking ill just redo the config
```
apt-get install libpam-ldap libnss-ldap
```

but no GUI config comes up, why is this? and how do i get it back?

thanks in advance

---

### Post by phoenix24x on 2007-10-11
a gentle bump...please help

---

