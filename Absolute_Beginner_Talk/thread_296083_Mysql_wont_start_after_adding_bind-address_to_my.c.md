---
title: "Mysql wont start after adding bind-address to my.cnf"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by audun1 on 2006-11-09
Hello.
I followed another tread today so i can connect remote to my mysql server.

I added bind-address = 192.168.2.187 to my.cnf but the mysql server faild to start.
I also tried bind-address = all but nothing work.
I want every computer on my network 192.168.2.% to connect to this mysql server.

Can someone help me pleas?

Thanks

---

### Post by adwait on 2006-11-09
Bind address is supposed to be the address to which MySQL listenings if I am not mistaken. ie: The IP address of the machine that is running mysql...

---

### Post by audun1 on 2006-11-09
That was strange.
I am sure you are right, but I had this problem for 6 month ago and then i edit a conf file and every thing worked.

How can i get the mysql to allow other computers on the network to connect to the base?

I downloaded the mysql-administrator and the tcp is enabled.

Thanks for any help.

---

### Post by adwait on 2006-11-09
Well, change the bind address to the IP of you computer and make sure that IP is reachable frmo the network. Also, you need to grant permissions to databases to different users eg
```
grant all on *.* to root@192.168.2.%
```

This will alow the person with username root to access any database from any computer on this network.

EDIT: the granting priveleges has to be done from inside mysql terminal by runnomg
```
mysql
```

Also you can probably grant the priveles using the graphcial frontends avaialable for administering the mysql server.

---

### Post by audun1 on 2006-11-09
Hello.
I have tried a lot now and I talk about the graphical initerface :D

[[img]http://bildr.no/thumb/18945.jpeg[/img]](http://bildr.no/view/18945)

This is how my mysql administrator looks like.

I think i have done everything logical in my head now.

adwait:
grant all on *.* to root@192.168.2.%

in terminal or in a config file?


Thanks.

---

### Post by adwait on 2006-11-09
The grant all.... is supposed to be entered in the myql terminal. But from the looks of the screenshot you posted, the uers "root" and "mythtv" seem to be configured correctly. Anyway, your mysql server seems to be starting now right? So what errors do you get when you try to connect to it?

---

### Post by audun1 on 2006-11-10
Yes my mysql server is starting now after I removed the bind-address.

The error I get is this:
Could not connect to MySQL instance at amdx2.
Error: Can't connect to MySQL server on 'amdx2' (61)
(code 2003)


Thanks


EDIT: If I use the mysql admin tool from the computer the mysql base is on and instead of localhost type the ip 192.168.2.140 i get the same error.

---

