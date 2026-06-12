---
title: "command not found message when trying to restart apache"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by andalu on 2007-12-11
When I attempt to restart apache from the terminal, I get the following message:

stephen@ubuntu-linux:~$ sudo /etc/int.d/apache2 restart
sudo: /etc/int.d/apache2: command not found

I'm not sure what I'm doing wrong.

Thanks for any help.

---

### Post by monktbd on 2007-12-11
the correct location of the startscript is
```
/etc/init.d/apache2 restart
```

---

### Post by andalu on 2007-12-11
thanks alot for your help, it worked.

---

