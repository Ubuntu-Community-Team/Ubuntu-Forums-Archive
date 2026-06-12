---
title: "Can't install  404 Not Found [IP: 91.189.88.31 80]"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by jcolo on 2007-06-12
Hi I am trying to install a php-cli but I want to download the packages even though the system stubbornly tries to install from a CD that is not there any more in the server.


I type

 [INDENT][INDENT]sudo apt-get -d install php5-cli
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libapache2-mod-php5 php5-common php5-mysql php5-mysqli
Suggested packages:
  php-pear
The following NEW packages will be installed:
  php5-cli
The following packages will be upgraded:
  libapache2-mod-php5 php5-common php5-mysql php5-mysqli
4 upgraded, 1 newly installed, 0 to remove and 32 not upgraded.
Need to get 4826kB of archives.
After unpacking 5140kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-cli 5.1.6-1ubuntu2.4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-mysqli 5.1.6-1ubuntu2.4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-mysql 5.1.6-1ubuntu2.4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libapache2-mod-php5 5.1.6-1ubuntu2.4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-common 5.1.6-1ubuntu2.4
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.1.6-1ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.1.6-1ubuntu2.4_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysqli_5.1.6-1ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysqli_5.1.6-1ubuntu2.4_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.1.6-1ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.1.6-1ubuntu2.4_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.4_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.4_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Some files failed to download
[/INDENT][/INDENT]

any hints ?? how is the best way to force download of packages to install... instead of letting the system relay on the pkg db/ cdrom ???

Many thanks.

JCG

---

### Post by useResa on 2007-06-12
It could be that you have a typo in your sources.list (the file that contains the location of the repositories). Could you open a terminal and issue the command ```
cat /etc/apt/sources.list
``` and post the result?

---

### Post by MenZa on 2007-06-12
It would seem that the file doesn't exist (duh)---perhaps there's a repository problem. I suggest running *sudo apt-get update*, then try again: *sudo aptitude install php5-cli*.

If that doesn't do it, try again in a few hours.

---

### Post by jcolo on 2007-06-12
thanks  

sudo apt-get update and then sudo apt-get upgrade did the work.

It worked however I do not know how nor can repeated....

Up and running !!  Many thanks.

JCG

---

