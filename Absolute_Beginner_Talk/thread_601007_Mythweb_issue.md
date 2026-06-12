---
title: "Mythweb issue"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-11-02
[PHP]blake:~$ sudo /etc/init.d/apache2 reload
apache2: Syntax error on line 295 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enable: No such file or directory
   ...fail!
[/PHP]

I was trying to edit this file to add my servername and think I inadvertenly deleted a line. Did not back up either. Can someone please post there line 295 or complete file. 

Thanks

---

### Post by Clickbg on 2007-11-02
i use vhosts, but that line should look like this

ServerName [www.example.com](www.example.com)

if line

Listen 80

is defined before, else 

ServerName [www.example.com:80](www.example.com:80)

---

### Post by jba6511 on 2007-11-02
thanks but line 295 is the following:

# Include the virtual host configurations:
Include /etc/apache2/sites-enable

Is this how it should look?

---

### Post by jba6511 on 2007-11-03
bump

---

### Post by jba6511 on 2007-11-04
fixed. New problem now but will start another thread.

Include /etc/apache2/sites-enabled/[^.#]*

---

