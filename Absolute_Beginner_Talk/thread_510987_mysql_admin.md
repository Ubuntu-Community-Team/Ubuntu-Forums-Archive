---
title: "mysql admin"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by doughardy on 2007-07-27
running >Linux ubuntu 2.6.20-15-server

---

### Post by Mornedhel on 2007-07-27
Something's missing here... A question perhaps ?

---

### Post by doughardy on 2007-07-27
running >Linux ubuntu 2.6.20-15-server

i am using a SSH Secure Shell Client and putty  from the xp machine

everything on ubuntu server works fine eg;  web server , forum  bf2 game server.

the problem i have is  the mysqladmin 1.2.9  i have on the xp comp  will not connect to the ubuntu server

ERROR  >  host xp comp is not allowed to connect to this mysql server

the mysql  is running on ubuntu and the login details in mysqladmin are definatly correct 

anyone have anyideas to what maybe causing this 
 thx very much  everyone:)

---

### Post by doughardy on 2007-07-27
> **Mornedhel said:**
> Something's missing here... A question perhaps ?

sorry Mornedhel getting info on server for another post

---

### Post by Bachstelze on 2007-07-27
Threads merged.

---

### Post by kngunn on 2007-07-27
I'm not completely clear on your setup, but let me dive in anyway...

You trying to connect to the MySQL server from Windows?  If so, do you have the MySQL port open (3306).

Try making a telnet connection to port 3306.  You should see your MySQL version number returned and then possibly some gibberish.

```
telnet myserver.domain.name 3306
```

If you can't connect you need to open the port.

---

### Post by doughardy on 2007-07-27
G&#9830;Host 'dougysmaincomp' is not allowed to connect to this MySQL server

Connection to host lost.

>telnet 192.168.1.64:3306
Connecting To 192.168.1.64:3306...Could not open connection to the host, on port
 23: Connect failed

i will open the port  and try again later

---

