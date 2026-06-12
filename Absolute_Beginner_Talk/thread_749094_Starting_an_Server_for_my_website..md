---
title: "Starting an Server for my website."
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by lion21 on 2008-04-08
Well I am shifting to windows XP to the linux first time , main purpose  is to host my website from home which requres

Apache
PHP
MySql
Perl

So how to go ahead with it ??

thanks in advance.

---

### Post by wormser on 2008-04-08
Here is a [guide]("http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html").

---

### Post by louieb on 2008-04-08
Since your a 1st time Linux user go ahead and do a normal Ubuntu desktop install.  The advantage over a server install is you'll have a GUI to use - not just the command line.  

then ```
sudo tasksel install lamp-server
```
or to a full list of prepared package bundles 
```
sudo tasksel
```

Heres some more hints on where to go from there.
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Also check out Wormser's link and in particular the part about [B]installing webmin.
[/B]Good luck.

---

### Post by hyper_ch on 2008-04-08
why recommending webmin?

---

### Post by Joeb454 on 2008-04-08
Webmin is a pretty easy way to manage Apache & co from a web based interface, I'd imagine that way you won't have to ssh to the server to manage it remotely (i.e. away from the home network) :)

---

### Post by hyper_ch on 2008-04-08
well, if you host 1 site what do you need to manage from apache anyway?

---

### Post by louieb on 2008-04-08
webmin doesn't just do Apache. it has pages for ftp, dns, samba, and a few other servers. If nothing else it give you an idea of what kind of things can be configured in the various types of servers. 

:lolflag:For me its just another toy er tool.

---

### Post by lion21 on 2008-04-08
thnaks guyz for an overwhelming  response  , i find this tutorial really good

[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html)

---

### Post by hyper_ch on 2008-04-08
I know what webmin does, but just for getting 1 page up and running it's overkill, adds too much unnecessary complexity, ....

---

