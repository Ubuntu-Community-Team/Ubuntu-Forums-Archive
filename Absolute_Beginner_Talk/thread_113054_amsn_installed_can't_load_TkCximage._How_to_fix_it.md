---
title: "amsn installed: can't load TkCximage. How to fix it ?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-05
Thank you

---

### Post by patrick295767 on 2006-01-05
Is it this to solve it:
> "make sure u have tk-devel & tcl-devel packages installed and Type make as root."

---

### Post by patrick295767 on 2006-01-05
I installed : 
```
apt-get install tk8.3-dev
apt-get install libreadline4-dev 
apt-get install gcc
apt-get install flex
```
  
And result:
Still the same error :
can't load tkcximage... 
 
Blocked like mentioned in other websites from google search...

---

### Post by gigiolin on 2007-12-11
it's easy, enter the next lines in a terminal:

sudo mv /usr/bin/wish /usr/bin/wish-bak
sudo ln -s /usr/bin/wish8.4 /usr/bin/wish

Byte!!

---

### Post by israel1601 on 2008-04-11
GET HERE: aMSN 0.98SVN WITH AntiAliase Installer

[http://www.mediafire.com/?6l2dxbrbkmn](http://www.mediafire.com/?6l2dxbrbkmn)

Command Line: 

To Install: dpkg -i --force- aMSN-0.98SVN-10-03-2008-tcl-tk8.6_libsnack-2.noarch.deb
To uninstall:  dpkg -r --force- amsn-0.98svn-10-03-2008-tcl

Open aMSN, go in Account > preference > Advanced

Search by TLS, put /usr/local/amsn/share/amsn/tls1.50
Save and Close.

Enjoy it.

---

### Post by Claus7 on 2008-04-11
Hello,

I did this:
[http://ubuntuforums.org/showthread.php?t=712425&highlight=amsn+dapper](http://ubuntuforums.org/showthread.php?t=712425&highlight=amsn+dapper)

(under Also in...)

Regards!

---

