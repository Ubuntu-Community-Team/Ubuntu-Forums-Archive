---
title: "can't connect to mysqlserver"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by ikkem on 2007-05-24
Hi....
I installed mysql but localhost can't connect to to mysql this is the error message I get 
>  mysqladmin: connect to server at 'darkstar' failed
error: 'Host 'localhost' is not allowed to connect to this MySQL server'
 

Hopefully someone can help me I have been at it for two days now I searched google and clusty but no luck yet...
Thanks in advance

---

### Post by ikonia on 2007-05-24
1.) check your spelling of localhost if your inputting it manually

2.) try this command "mysql -u root -p" and see what it does.

---

### Post by ikkem on 2007-05-24
I am trying to set a password for root on localhost this is the output of the error message
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)' 
thanks in advance

---

### Post by ikkem on 2007-05-24
> **ikonia said:**
> 1.) check your spelling of localhost if your inputting it manually

2.) try this command "mysql -u root -p" and see what it does.

thanks for reacting
the spelling was ok....

the output of the command is 
> $ mysql -u root -p
Enter password:
 

---

### Post by ikonia on 2007-05-24
well hit enter for the password "no password in reality"

then if that works use -u root -p on the mysqladmin command and you golden.

---

### Post by ikkem on 2007-05-24
thanks for reacting it seems to work now....

---

### Post by VorDesigns on 2007-05-26
OK, I know how to enter the destination IP and port correctly.
-
My problem is the the remote client isn't allowed to connect to the server. 

Where would I set client access list or subnet or IP?

Thanks in advance.

Both systems I try using, one with Aqua Data Studio (Win32) and the other mysqladmin (Dapper) get similar errors:
Aqua Data Studio gets the error 
```
Connection failed:  Data source rejected establishment of connection, message from server:  "Host 'xxx.xxx.xxx.xxx' is not allowed to connect this MySQL Server
"
```
mysqladmin gets the  error
```
Client cannot connect to host 'xxx.xxx.xxx.xxx'
MySQL Error Nr. 1130
Host 'xxx.xxx.xxx.xxx' is not allowed to connect this MySQL Server
```

One point of note; the MySQL server is on a separate network 172.32.x.x vs. the clients; both clients live on the same private network 172.16.x.x but one host looks like it comes from the WAN, the other looks like is comes from the 172.16.x.x network.  This is how it is supposed to look but, if this is the problem, I can make the traffic look it is coming from the development LAN gateway for MySQL traffic in order to connect.

I would rath know where to adjust the server.

---

