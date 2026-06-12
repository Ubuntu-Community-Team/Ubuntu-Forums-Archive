---
title: "Mythweb password"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by besmith2@hotmail.com on 2007-10-18
Ok I changed mythtv db user password and now I can't get into mythweb help....

---

### Post by besmith2@hotmail.com on 2007-10-18
sigh

---

### Post by Tteddo on 2007-10-18
Can you go in and set it to the new password in mythtv-setup?

---

### Post by Tteddo on 2007-10-18
Or, go into mysql and put it back. In a terminal window type:
```
mysql -u root 
```
then:
```
 SET PASSWORD FOR mythtv@localhost=PASSWORD('new_password');
```

If you are running Mythbuntu I think it just uses the first username you used when you installed it instead of the user mythtv.

```
exit
```
Gets you out of mysql.

---

