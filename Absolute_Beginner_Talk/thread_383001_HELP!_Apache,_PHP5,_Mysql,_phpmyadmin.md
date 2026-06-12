---
title: "HELP! Apache, PHP5, Mysql, phpmyadmin"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-03-12
Hi, 

I have installed Apache, PHP5, Mysql, phpnyadmin, proftpd. 

And I am having a bit of trouble using it all. 

I cant change any files in the “/var/www/” directory 

I get a message that I am not the owner. 

I cant login to phpmyadmin. Is there some default admin username and password?

And proftpd, well I have installed it but I cannot start it. 
Let alone try to change its directory to “/var/www/” which is what I wanted to do…

Is there any tutorials that I can read? Or can someone give me a few pointers. 

I’m basiclly just trying to setup a home http server. 

Cheers, 

Loic.

---

### Post by houstonbofh on 2007-03-12
You can not write to /var/www as a user.  You have to be root.  You can set permissions on /var/www to allow access, or you can change ownership.  Or, you can run a root file manager with the command 'gksu nautilus' and change things like that.

For phpmyadmin to work, you have to log in with a username and password for mysql.  Default there is no password, so try root with no password.

For ProFTPd go to System -> Administration -> Services, and enable it.

---

### Post by LoicNyssen on 2007-03-12
To enable ftp, can this be done remotely using ssh access?

---

### Post by houstonbofh on 2007-03-17
Yes, actually.  SSH in with X tunneling support.  'ssh -X my.ip.address.com'  then type 'gksu services-admin' and you are off.

---

