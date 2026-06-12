---
title: "python is frustrating"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-16
I keep trying to get python to install on my PC, but it never installs correctly. I am so frustrated now because python is a dependency for *EVERYTHING*.....
:( 
Someone pleasse take a look and help me fix this psychotic computer...:mrgreen: 

root@my-laptop:~# apt-get python2.3-4suite -install
E: Command line option 'i' [from -install] is not known.
root@my-laptop:~# aptitude -vv reinstall python2.3-4suite
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
python2.3-4suite is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
root@my-laptop:~# aptitude -vv install python2.3-4suite
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  python2.3-4suite
The following packages are SUGGESTED but will NOT be installed:
  postgresql
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6198B of archives. After unpacking 41.0kB will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe python2.3-4suite 0.99cvs20050418-2ubuntu1 [6198B]
Fetched 6198B in 7s (807B/s)
Selecting previously deselected package python2.3-4suite.
(Reading database ... 181192 files and directories currently installed.)
Unpacking python2.3-4suite (from .../python2.3-4suite_0.99cvs20050418-2ubuntu1_i386.deb) ...
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.3-4suite
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.3-4suite

---

### Post by jordanmthomas on 2006-10-16
> root@my-laptop:~# apt-get python2.3-4suite -install
E: Command line option 'i' [from -install] is not known.
The proper syntax would have been:
```
apt-get install python2.3-4suite
```
..just so you know.  This still won't fix your problem though.

Do you actually need this package?  Python should already be installed.
According to Debian, this package:
```
An open-source platform for XML and RDF processing for Python 2.3

4Suite is a Python-based toolkit for XML and RDF application development. At the core of 4Suite is a library of integrated tools (including convenient command-line tools for XML processing, implementing open technologies such as DOM, RDF, XSLT, XInclude, XPointer, XLink XPath, XUpdate, RELAX NG, and XML/SGML Catalogs.

Layered upon this is an XML and RDF data repository and server. The server supports multiple methods of data access, query, indexing, transformation, rich linking, and rules processing. It provides the data infrastructure of a full database management system, including transactions and concurrency support, access control and a variety of management tools. For purposes of integration with other tools, it supports remote, cross-platform and cross-language access through HTTP (including native SOAP and WebDAV), RPC, FTP and CORBA. It offers APIs in Python, HTTP, SOAP and XSLT.

This package is built for Python 2.3.x. 
```

Your package isn't actually installing python, but XML bindings and some other things for python.

Can you run python from a command line?  If so, it is installed.  For the time being, I would not install python2.3-4suite and would remove it since it's been causing you such troubles.

---

### Post by jordanmthomas on 2006-10-16
Oh, and this may help you install it if you really want it installed:

```
mkdir /etc/alternatives/4ssd
```
Things may not work correctly, but at least the installer will shut up.

---

### Post by saintj0n on 2006-10-17
I actually can run python. I write scripts from time to time. However, I frequently hit errors when installing packages and it always names python2.3-4suite as being the package in question. I don't know what is causing it but I suspect it is the reason why I can't run shockwave on my computer. I like to watch episodes of the tv shows that I missed on the abc.com website but they aren't working. Flashplayer is installed though. I really don't know enough about Linux to know what role the different plug ins and things do.

---

### Post by jordanmthomas on 2006-10-17
To run shockwave,  you have to run the Windows version of Firefox in wine because Adobe doesn't make Shockwave for Linux.
Look around, you can find guides on it pretty easily.

If you're just using python for scripts and whatnot, get rid of that python2.3-4suite balogna.  

```
aptitude purge python2.3-4suite
```

---

### Post by saintj0n on 2006-10-17
ok...got it done now. I can still use my python and xml IDE stuff though can't I? I eventually hope to start coding xml on this computer. I'm pretty sure it wants python2.3-4suite when I try installing anything with xml.

Btw, won't the installer notice that the python2.3-4suite dependency is not installed and print a complaint message on the terminal screen?

---

### Post by jordanmthomas on 2006-10-17
This may or may not work, but shouldn't mess anything up.
```

touch /etc/alternatives/4ssd # create this file so dpkg won't complain about it
apt-get clean # get rid of old downloaded packages
apt-get update # get newest list of packages
apt-get install python2.3-4suite

```
and pray.

To answer your second question:  yes, if it is a dependency for your IDE it will complain and you will have to install it.  I'm sorry you're having such trouble with this.  I'm using edgy and the same package (but for python 2.4) installed fine for me, so I don't know why it isn't working.

---

