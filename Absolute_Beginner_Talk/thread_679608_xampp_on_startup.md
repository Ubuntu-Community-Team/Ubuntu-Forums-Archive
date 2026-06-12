---
title: "xampp on startup ???"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Jonian on 2008-01-27
Hi , i want to start xampp when ubuntu starts :confused::confused: i'v tried with bashrc but it says 

> You need to start XAMPP as root!

and i want also a link to be opened when i start my PC , beucase i have a dynamic IP and i got a link to update it but i have to open it manually :(:(

---

### Post by Jonian on 2008-01-27
delete the topic please... i found the solution :)

---

### Post by indytim on 2008-01-27
You might consider marking the topic solved and posting the solution you found.  That way your "find" may benefit someone else in the future with the same initial problem.

IndyTim

---

### Post by Jonian on 2008-01-28
To make xampp as a service 
> sudo ln -s /opt/lamp/lamp /etc/rc2.d/S99lampp 

to make the link to open on system startup
> 
System -> Preferences -> Sessions -> + ADD -> COMMAND = firefox [http://www.link.com](http://www.link.com)

---

