---
title: "How do I check which ports are open or forwarded in my router?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by nickle on 2006-03-25
Which command(s) can I use to check the status of ports in my router and software firewall?

---

### Post by dvarsam on 2006-03-25
[QUOTE=nickle]Which command(s) can I use to check the status of ports in my router and software firewall?[/QUOTE]

Visit the site:

[www.grc.com](www.grc.com)

There is a "shields up" utility that checks ALL your Router's ports to see if you have opened any of them.

Good Luck.

---

### Post by tahitiwibble on 2008-01-25
Would somebody be kind enough to explain very briefly what this means :

dad@dad-desktop:~$ netstat -l -t
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 *:44919                 *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:2207          *:*                     LISTEN

---

### Post by tahitiwibble on 2008-01-25
sorry! but ........... bump

---

### Post by equity on 2008-03-28
I have a very bad feeling, I chose the shields up utility and it says to me:

-----------------------------------------------------------------------------------------------------------------------------
Greetings!

Without your knowledge or explicit permission, the Windows networking technology which connects your computer to the Internet may be offering some or all of your computer's data to the entire world at this very moment!

-----------------------------------------------------------------------------------------------------------------------------

Should I be worried about that??? I dont feel very secure at the moment.

---

### Post by stchman on 2008-03-28
> **nickle said:**
> Which command(s) can I use to check the status of ports in my router and software firewall?

Login to your router (typically 192.168.1.1) and go to the port forwarding section.  By default there are no ports forwarded in your router.

---

### Post by equity on 2008-03-28
> Login to your router (typically 192.168.1.1) and go to the port forwarding section. By default there are no ports forwarded in your router.

Okay... that is an option but not a very affective way.
1. not everyone is allowed to access the router's configuration
2. some router's software are bugged, for example many zyxel routers, I forward some ports in the config and they are not forwarded instantly (can be fixed via a software update)

---

### Post by stchman on 2008-03-28
> **equity said:**
> Okay... that is an option but not a very affective way.
1. not everyone is allowed to access the router's configuration
2. some router's software are bugged, for example many zyxel routers, I forward some ports in the config and they are not forwarded instantly (can be fixed via a software update)

Well the poster did say "my" router.  I was assuming that it belonged to them.

---

### Post by dcstar on 2008-03-28
> **equity said:**
> Okay... that is an option but not a very affective way.
1. not everyone is allowed to access the router's configuration
2. some router's software are bugged, for example many zyxel routers, I forward some ports in the config and they are not forwarded instantly (can be fixed via a software update)

It is the only way.

**You** posted that **you** "dont feel very secure", so do something about it rather than make excuses.

---

