---
title: "Permissions driving me crazy"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Rhodan on 2007-05-07
I've installed Feisty on my laptop. I'm battling to get anything done with regards to installing apps etc. The problem is permissions. Using "su" it asks me for a password, which I enter my default password for logging in, the only password I used whilst setting up the install, and it doesn't accept it.

Having to use "sudo" all the time is extremely annoying.

Please help.

---

### Post by k1001001 on 2007-05-07
You can log in as a root user by typing "sudo -i" and then your root password. Then you don't have to keep typing "sudo".

---

### Post by aysiu on 2007-05-07
These two links should prevent you from going crazy:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by jargoman on 2007-05-07
I use 
$ sudo su

then MY password! not root. A little hack I figured out

---

### Post by jargoman on 2007-05-07
or the correct way

$ sudo -s

---

### Post by surfjdh on 2007-05-07
yeah its a pain but its there for a reason.   Its why viruses have such a hard time fcuking up a linux box.

---

### Post by Rhodan on 2007-05-07
Thanks I'll check it out.

---

