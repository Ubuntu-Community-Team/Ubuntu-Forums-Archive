---
title: "Apache installed but not working"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by hartnady on 2006-01-25
Hello Ubuntu Community...!

I just installed Ubuntu 5.10 and now I wanna start setting up Apache, PHP, MySQL.

I installed Apache2 using the default installer but when I type [http://localhost](http://localhost) in FireFox, I get the error **The connection was refused when attempting to connect to localhost**. Normal websites work fine.

Any ideas as to why this is? Also, what is the command line from a terminal screen to start/restart/stop Apache?

Many thanks.

---

### Post by kaamos on 2006-01-25
have you tried [http://127.0.0.1/](http://127.0.0.1/) ? 

Apache can probably be restarted with "sudo /etc/init.d/apache restart"

---

### Post by hartnady on 2006-01-25
[http://127.0.0.1](http://127.0.0.1) not working either (same error: cannot connect to 127.0.0.1)

In ubuntu GUI I went to SYSTEM -> ADMINISTRATION -> SERVICES

Apache2 is listed and checked as a service.

[b]mark@MARK:/$ sudo /etc/init.d/apache restart
Password:
sudo: /etc/init.d/apache: command not found[/b]

---

### Post by kaamos on 2006-01-25
Sorry, the file is etc/init.d/apache2 with apache2.

---

### Post by hartnady on 2006-01-25
Okay... did that... no error was reported (which means that it is apache2) but still...

[http://localhost](http://localhost) not working!

---

