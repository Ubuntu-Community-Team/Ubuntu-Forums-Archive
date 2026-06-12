---
title: "Installation of python2.4-4suite fails"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by rccharles on 2006-10-18
I cannot seem to install the package python2.4-4suite.  

The package isn't found.  Why?

Here is the sources.list file:
> 
root@kubuntu:~# cat /etc/apt/sources.list
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse



Here is the install.

> 



root@kubuntu:~# aptitude install python2.4-4suite
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "python2.4-4suite"


Here are some searches:

> 
root@kubuntu:~# apt-cache search python2.4-4suite
root@kubuntu:~# apt-cache search python2.4-4
root@kubuntu:~# apt-cache search python2.4-
python2.4 - An interactive high-level object-oriented language (version 2.4)
python2.4-dbg - Debug Build of the Python Interpreter (version 2.4)
...


Here is the package in packages.
[http://packages.ubuntu.com/dapper/python/python2.4-4suite](http://packages.ubuntu.com/dapper/python/python2.4-4suite)

Robert

---

### Post by dbd on 2006-10-18
I have no idea why it's not there (or what it is!), but you could just download it manually then install the deb.
Download it from :
[http://packages.ubuntu.com/dapper/python/python2.4-4suite](http://packages.ubuntu.com/dapper/python/python2.4-4suite)
then use this command to install it:
sudp dpkg -i python2.4-4suite

---

