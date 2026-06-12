---
title: "user with some privileges"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-03-30
Okay so I just got my SSH server up and running (finally) and gave my friend the info he needed to connect. He thought it would be a good joke to halt my system...

I want to try to prevent this. I created a separate user to run the ssh service and had to give it administrative privileges in order to start the service. Is there another way to start the service without using sudo? or using chmod?

---

### Post by collinp on 2008-03-30
Im sorry but as far as i know there is no way to give a account root status, its a security precaution built into Ubuntu. Maybe someone else will know a way, but i dont.

---

### Post by elchico04 on 2008-03-30
?? that wasn't was I was asking for.
I want a user to be able to start a certain process that I can only start by using sudo without having admin privs.

---

### Post by collinp on 2008-03-30
Yes, sudo gives you root status. So to be able to start the process without using sudo you would need a user with root status, as far as i know.

---

### Post by pseudo-random on 2008-03-30
So you need to edit your /etc/sudoers file by the sounds of it.
There's detailed descriptions within the file on how to do it.
Ensure you use the correct program to edit it:  visudo.

---

### Post by elchico04 on 2008-03-30
thanks. that was what I needed to do.

This tutorial explains it.
[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)

---

