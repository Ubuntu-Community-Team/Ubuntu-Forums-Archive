---
title: "sources or proxy failure"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-04-05
ok...
i am trying to install the basics on my server... but i am not succeding,..

i cant figure out if i am using dead repositories or if its the proxy that is not well defined.

here is what i have inserted
```

export http_proxy="proxy.domain.com:8080"
sudo apt-cache search mysql
```


I get this... wich is not satisfatory :(

```
 p@ubuntu:~$ sudo apt-cache search mysql 
openoffice.org2-base - OpenOffice.org office suite - database 
python-mysqldb - A Python interface to MySQL 
mysql-common - mysql database common files (e.g. /etc/mysql/my.cnf) 
libmysqlclient14 - mysql database client library 
libmysqlclient12 - mysql database client library 
python2.4-mysqldb - A Python interface to MySQL 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy/main Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy/restricted Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy/universe Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy/multiverse Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy-updates/main Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy-updates/restricted Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy-updates/universe Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://pt.archive.ubuntu.com]("http://pt.archive.ubuntu.com/") breezy-updates/multiverse Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory) 
W: Couldn't stat source package list [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory) 
```

here is my sources.list just generated 10 minutes ago using source-o-matic

```
 # Automatically generated sources.list 
# [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") 
# 
# If you get errors about missing keys, lookup the key in this file 
# and run these commands (replace KEY with the key number) 
# 
# gpg --keyserver subkeys.pgp.net --recv KEY 
# gpg --export --armor KEY | sudo apt-key add - 
 
# Ubuntu supported packages (packages, GPG key: 437D05B5) 
deb [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy main restricted 
deb [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy-updates main restricted 
deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted 
 
# Ubuntu supported packages (sources, GPG key: 437D05B5) 
deb-src [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy main restricted 
deb-src [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy-updates main restricted 
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted 
 
# Ubuntu community supported packages (packages, GPG key: 437D05B5) 
deb [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy universe multiverse 
deb [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy-updates universe multiverse 
deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe multiverse 
 
# Ubuntu community supported packages (sources, GPG key: 437D05B5) 
deb-src [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy universe multiverse 
deb-src [http://pt.archive.ubuntu.com/ubuntu]("http://pt.archive.ubuntu.com/ubuntu") breezy-updates universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe multivers
```

---

### Post by wylie348 on 2006-04-05
You should try:

export http_proxy=http://192.168.0.12:8080
export ftp_proxy=http://192.168.0.12:8080

replace 192.168.0.12:8080 with your proxy IP and port

You are missing the http:// from your export command.

You probably do not need the ftp stuff, unless some of the repositories in your sources.list contain ftp sites.

This should work, and if not, I would check to see that your networking is up.  Finally, when you type these export commands in, you probably want to refresh your repository list by doing:

sudo apt-get update

Enjoy!
:)

---

### Post by pedrotuga on 2006-04-05
[quote=wylie348]You should try:

export http_proxy=http://192.168.0.12:8080
export ftp_proxy=http://192.168.0.12:8080

replace 192.168.0.12:8080 with your proxy IP and port

You are missing the http:// from your export command.

You probably do not need the ftp stuff, unless some of the repositories in your sources.list contain ftp sites.

This should work, and if not, I would check to see that your networking is up. Finally, when you type these export commands in, you probably want to refresh your repository list by doing:

sudo apt-get update

Enjoy!
:)[/quote]


Aaaaaaaaaaaaaaaaahhh!!!!

apt-get update!!!!
finaly!!!!
that command was missing... damn i tryed soooo many diferent sources.list
loooll

---

### Post by venkateshkumar on 2008-01-28
Hi,

While I am trying to send about ten files from my database to third party ftp site in daily basis.sometimes only one particular file transfer gets failed.

Any one can help me plese in solving this issue.

thanks,
venkatesh

---

