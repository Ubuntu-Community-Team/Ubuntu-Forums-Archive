---
title: "Installed Lamp using really easy command, now problems..."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-16
I installed LAMP using this:

```
sudo apt-get install phpmyadmin
```

After that, everything worked great. But when I go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), it asks for a username and password. I typed in my Ubuntu login and pass, and I got this:

```
Error
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
```

It's important I get mySQL running ASAP, can someone help?

---

### Post by llamakc on 2007-06-16
For starters, is the mysql daemon running? Open the terminal and type:

ps aux | grep mysql

to start.

---

### Post by bobplano on 2007-06-16
umm to my knowledge phpmyadmin doesn't install the whole lamp. try running the command ```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
``` if that installs anything then you were missing things. you might also need to configure some things before it will work

---

### Post by alecwh on 2007-06-16
Ok, it's installing stuff now.

After that, what do I do?

---

### Post by alecwh on 2007-06-16
Thanks very much, everything is working. :D

---

