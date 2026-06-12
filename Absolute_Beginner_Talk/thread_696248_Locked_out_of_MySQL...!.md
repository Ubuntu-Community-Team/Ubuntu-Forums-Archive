---
title: "Locked out of MySQL...!"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Kareeser on 2008-02-13
Hey everybody! *jives with his ¨first cup of ubuntu¨*

So I am new to Linux... and I am making a web server/php/SQL

So I downloaded and installed Ubuntu Server Edition.

Everything is great... installed GNOME, etc etc.

Problem is...! I´m somehow locked out of my own SQL server. It won´t take root/(blank) as the login combo, and I´m POSITIVE I did not change it because I don´t know how. =P

Any idea what I´m supposed to do now? phpMyAdmin is set-up correctly, but can´t access the server for the above-mentioned reason... :S!

Thanks for your help!
- Kareeser

---

### Post by macogw on 2008-02-13
The root password is locked, not an empty string.  You login as yourself, then use "sudo" ("superuser do"...like "Simon says") to execute root commands.  See here:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information about sudo.

---

### Post by Kareeser on 2008-02-13
Hm... I´m actually trying to access the SQL database through phpMyAdmin. Even when I run the setup script again using the config method, it won´t allow ¨root¨ to log in... hrm.!

---

### Post by emarkd on 2008-02-13
If you've never set a root password, it should just be empty, as in not required.  If that isn't working through phpmyadmin, try setting a root password.  From your terminal, run:

```
mysqladmin -u root password NEWPASS
```

where NEWPASS is what you want your password to be.

---

### Post by Kareeser on 2008-02-14
> error: 'Access denied for user 'root'@'localhost' (using password: NO)'

So it looks like the root password has been set, but I swear I have not...!!

Perhaps I should just install my LAMP server manually, eh?

---

### Post by Kareeser on 2008-02-15
Okay, so I started over and installed everything manually. Works like a charm 'cause the install asked to set the root password...

Weird how the original Ubuntu Server install didn't ask me...

---

