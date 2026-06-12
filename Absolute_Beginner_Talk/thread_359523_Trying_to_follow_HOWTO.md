---
title: "Trying to follow HOWTO"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Funbug on 2007-02-12
Trying to follow this HOWTO [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

All goes well until I get to this point & I get the following error message

[COLOR="Blue"]admin@Butterflytouch:~$ sudo mysqladmin -h butterflytouch.com -u root password *******
Password:
mysqladmin: connect to server at 'butterflytouch.com' failed
error: 'Host 'butterflytouch.com' is not allowed to connect to this MySQL server'
admin@Butterflytouch:~$[/COLOR]

Any ideas please.

Alan...

---

### Post by alphane on 2007-02-12
Not a MySql wizard, I'm an ASP/MSSQL/VB man by trade (as much as I dislike them nowadays)  but I would suggest trying the actual server IP address instead of the domain name.

---

