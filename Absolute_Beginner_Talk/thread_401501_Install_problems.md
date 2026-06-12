---
title: "Install problems"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by dlittle111 on 2007-04-04
I installed Ubuntu server 6.06, choosing the Lamp installation. During boot up, it starts the Mysql server and Apache. Then it runs the local boot scripts (etc/rc.local). After that, it displays "Ubuntu 6.06.1 LTS [network name] tty1"

It stops there. If i hit "enter" it asks for my login. I enter the login I set up, hit enter, it asks for my password. I enter that, but I always get login incorrect, even though I am entering exactly the username and password I set up during installation. I've reinstalled twice now and still get the same thing. Any suggestions?

---

### Post by drakazz on 2007-04-04
> **dlittle111 said:**
> I installed Ubuntu server 6.06, choosing the Lamp installation. During boot up, it starts the Mysql server and Apache. Then it runs the local boot scripts (etc/rc.local). After that, it displays "Ubuntu 6.06.1 LTS [network name] tty1"

It stops there. If i hit "enter" it asks for my login. I enter the login I set up, hit enter, it asks for my password. I enter that, but I always get login incorrect, even though I am entering exactly the username and password I set up during installation. I've reinstalled twice now and still get the same thing. Any suggestions?

Check capital letters and anything else that could not be correct, because the whole login system is case sensitive.
Also, try logging in as root and it might help you solve the problem.
When as root, you can do "su - username" and change the username's password with "passwd".

By the way, where are you logging in? Are you in a graphical login interface or the terminal?

---

