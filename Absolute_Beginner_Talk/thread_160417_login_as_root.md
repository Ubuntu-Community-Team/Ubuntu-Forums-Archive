---
title: "login as root"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by slimdog360 on 2006-04-14
I know this is going to sound stupid, but here it goes. How do I login as root, I know that the username is root, but whats the password. Ive tried password, nothing, default, everything underthe sun but I cant figure it out.
Thanks

---

### Post by dermotti on 2006-04-14
By default, Ubuntu doesnt use a root account. If you absolutly need one, you have to enable it.

Ubuntu uses **sudo**, so any command that you need root priveledges, jsut precede it with **sudo**

like

**sudo vi http.conf**

---

### Post by twirp on 2006-04-14
You don't
If you need to run something as root, enter (in the terminal):
sudo *command*
and if it asks for a password, enter your own

*Edit: There are too many people in this forum...*

---

### Post by gabruo on 2006-04-14
Basically you use 'sudo' in ubuntu instead of 'root' before issuing any terminal commands that would require root privledges.  Such as 'sudo apt-get install *' you will then be prompted for a password, your user password will do.  If you still want to enable root or root graphical login read the following.
[https://wiki.ubuntu.com/RootSudo?highlight=%28root%29](https://wiki.ubuntu.com/RootSudo?highlight=%28root%29)

---

### Post by aysiu on 2006-04-14
You may also want to read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Mustard on 2006-04-14
..and here is a link to something completely useless....

[http://www.intriguing.com/mp/](http://www.intriguing.com/mp/)

---

