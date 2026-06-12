---
title: "Installing PHP"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by kgls13349 on 2006-08-22
ok im a new user, i have used linux to a certain degree at college but i still considermyself a complete nOOb :D 
I wanted to setup a Small Linux powered Home server running Apache PHP Mysql to be able to do Database driven interactive webpages and also samba for filesharing

Now ive managed to get apache installed and running, and apparently Mysql cuz i cna log in as root to the mysql command line, but im having problems installing php, or rather getting apache to use it, i have no idea how to configure apache to use it :confused:  ive fought with it for ages but got nowhere ](*,) 
i was windering if anyone had any hints as to where im going wrong, the only error i get is 

"Unknown: failed to open stream: Permission denied in Unknown on line 
Warning:  Unknown: Failed opening '/var/www/php_test.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear')"

i installed apache and php at college but that was SuSe 8 and i did it use YaSt, im completely lost with how to configure it all on ubuntu :( 

Thank you for any comments :)

---

### Post by GeekSpeek'r on 2006-08-22
ok, do:

apt-get install mysql-common
apt-get install mysql-server
apt-get install php5   (or php4 if you like)
apt-get install samaba


That will start you nicely

---

### Post by az on 2006-08-22
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by kgls13349 on 2006-08-22
Thanks for the reply,
i tried what you said, it said that the newest versions were installed, but now apaches stopped working :confused:

Ahh thanks for the link, ill give it a try :)

---

### Post by kgls13349 on 2006-08-22
ok, ive followed them instructions, but everythings pretty much the same, when starting/stopping/restarting apache i get a comment that it couldnt find the fully qualified domain name and uses 127.0.0.1 instead, but that shouldnt stop php working in firefox on the server should it?

By the way im using Ubuntu 5.10 (?Breezy Badger :-s ) ill be honest i bourght linux format magazine and it came with it, i was fighting with mandriva linux before that, that wouldnt even acept the nvidia drivers for the motherboards chipset :rolleyes: 


thanks

---

