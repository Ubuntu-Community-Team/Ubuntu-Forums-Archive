---
title: "Mulitple /usr/sbin/apache2 -k start -DSSL running"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-12-05
Hi All,

[LEFT]I have multiple /usr/sbin/apache2 -k start -DSSL processes running on my apache2 server - Ubuntu 6.06 server.

Any ideas what it may be? As they are eating 160mb of ram!

Cheers

Robin
[/LEFT]

---

### Post by robinlennox on 2007-12-06
*Bump*

---

### Post by robinlennox on 2007-12-06
*Bump*

---

### Post by robinlennox on 2007-12-06
Any Ideas??????

---

### Post by rabrear on 2007-12-09
Hi Robin, 

When apache starts up the parent process starts multiple child processes to handle connections.
Spare (idle) child processes are started in order to cope with sudden increases in the number of client connections. 

Its normal to have multiple /usr/sbin/apache2 -k start -DSSL processes running: I currently have about 50 (on a heavily loaded server). You can change the number of processes that apache will start in /etc/apache2/apache2.conf:

```
# StartServers ......... number of server processes to start
# MinSpareServers ...... minimum number of server processes which are kept spare
# MaxSpareServers ...... maximum number of server processes which are kept spare
# MaxClients ........... maximum number of server processes allowed to start
# MaxRequestsPerChild .. maximum number of requests a server process serves
<IfModule prefork.c>
StartServers         5
MinSpareServers      5
MaxSpareServers     10
MaxClients          20
MaxRequestsPerChild  0
</IfModule>
```

also, earlier apache configs files have a good explanation of what these things do:

```
#
# Server-pool size regulation.  Rather than making you guess how many
# server processes you need, Apache dynamically adapts to the load it
# sees --- that is, it tries to maintain enough server processes to
# handle the current load, plus a few spare servers to handle transient
# load spikes (e.g., multiple simultaneous requests from a single
# Netscape browser).
#
# It does this by periodically checking how many servers are waiting
# for a request.  If there are fewer than MinSpareServers, it creates
# a new spare.  If there are more than MaxSpareServers, some of the
# spares die off.  The default values are probably OK for most sites.
# 
MinSpareServers 1
MaxSpareServers 5

#
# Number of servers to start initially --- should be a reasonable ballpark
# figure.
#
StartServers 1
```

Reducing these numbers will free up system resources, byt will also effect apache's performance.

Hope this helps

R

---

### Post by rudeboyintrouble on 2008-05-31
This answered my same question, thank you.

---

