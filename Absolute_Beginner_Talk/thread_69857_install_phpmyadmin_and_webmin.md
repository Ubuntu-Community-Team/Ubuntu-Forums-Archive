---
title: "install phpmyadmin and webmin"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by azuna on 2005-09-28
i want to create ubuntu as my webserver. now i use dynamic ip.

1. what must i do to create ubuntu as webserver (about set ip, register at freedns and etc?
2. how to install phpmyadmin and webmin?
3. what must i have before install phpmyadmin and webmin?

---

### Post by Jussi Kukkonen on 2005-09-28
1:If you have the option of using a static IP, do that -- using dyndns or something like it works, but it's still a hack. Otherwise you must update your dynamic IP to the dyndns service you use (if your router is not capable of this). There are a couple of programs in the repositories for this: ddclient, ez-ipupdate, ipcheck.
You'll need to open the relevant ports on your router if you have one.
[Edit: forgot the main point:]
You'll  need to install the web server of course. see [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

2 & 3: phpmyadmin and webmin are both in universe repository, so you can just use synaptic or 
```
apt-get install webmin phpmyadmin
```
You shouldn't need to do much else -- synaptic or apt-get will take care of dependencies.

---

### Post by cedjo on 2005-09-28
Hello.
I got ubuntu as a webserver for several month (I just change for Debian but it was just for fun, Ubuntu is able to make a good server as well)

I installed apache2 (webserver), mysql (DB), php4, vsftpd (FTP) ,postfix (mail),dovecot (SMTP),ddclient (for dynamic IP with dyndns.org) or noip2 (for no-ip.com dyn IP), phpmyadmin & webmin everything worked easily.

on howtoforge.com there's a good article on how to bring ubuntu as a "perfect server"

[http://www.howtoforge.com/perfect_setup_ubuntu_5.04]("http://www.howtoforge.com/perfect_setup_ubuntu_5.04")

First try with this article and if you have any problem, feel free to ask :)

---

### Post by matthewv on 2005-09-28
I configured dyndns with my router and then installed XAMPP from [the XAMPP website]("http://www.apachefriends.org/en/xampp-linux.html"). I followed all the instructions on the XAMPP site and ended up with a great, stable webserver.:)

---

### Post by azuna on 2005-09-30
> You'll need to open the relevant ports on your router if you have one.

what port? i'm use router dlink. how to open port?

---

### Post by cedjo on 2005-09-30
each service is using a specific port...
http:80
ftp:21
pop:110
imap:143
....
if your router is blocking the incoming aud outgoing traffic on a port the service will not be available. (firewall rules)
check the net or your dlink documentation to know how to configure those settings :smile:

---

