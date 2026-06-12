---
title: "Synaptic Package Manager"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Evelyn on 2007-08-15
I'm having problems with loading packages.  twice so far I've gotten this error message while trying to load two different packages.

Changes applied
Not all changes and updates succeeded.  For further details of the the failure, please expand the 'terminal' panel below.

There is too much in that window to type.  Please help!

---

### Post by Inxsible on 2007-08-15
what are the packages that you are trying to install ?

do you have the Add/Remove open at the same time?

---

### Post by Hobo Joe on 2007-08-15
Just copy and paste what it says, we'll try and figure it out for you. :)

---

### Post by Evelyn on 2007-08-15
The first problem I had with with loading the zope-zaaplugins package.
The second problem I had was with loading these pacakes: libasound2-dev, libasound2-doc, libasound2-plugins.  I did these two processes at different times.

I've tried several times to copy the text in the details window and I am not able to.  So here is my 
typing what it says:

Changes applied
Not all changes and updates succeeded.  For further details of the the failure, please expand the 'terminal' panel below.

Details:
(Reading database . . . 143588 files and directories currently installed.)
Preparing to replace libasound2 -dev 1.0.13-1ubuntu5 (using . . ./libasound2-dev_1.0.13-1ubuntu5 i386.deb) . . .
Preparing to replace libasound2-doc 1.0.13-1ubuntu5 (using . . ./libasound2-doc_1.0.13-1ubuntu5_all.deb) . . .
Preparing to replace libasound2-plugins 1.0.13-3ubuntu1 (using . . ./lubasound2-plugins_1.0.13-3ubuntu1_i386.deb) . . .
Unpacking replacement libasound2-plugins . . .
Setting up zope (2.6.4-1.8) . . .
/var/lib/dpakg/info/zope.config:96:arith: syntax error: "TRIES++"
dpkg: error processing zope (--configure):
 subprocess post-installation script returned error exit staus 2
dpkg: dependency problems prevent configuration of zope-zaaplugins:
 zope-saaplugins depands on sope2.7 ! zope (>= 2.6); however:
  Package zope2.7 is not installed.
  Package sope is not configured yet.
dkg: error processing zope-zaaplugins (--configure):
dependency problems - leaving unconfigured
Setting up libasound2-dev (1.0.13-1ubuntu5) . . .

Setting up libasound2-doc (1.0.13-1ubuntu5) . . .

Setting up libasound2-plugins (1.0.13-3ubuntu1) . . .
Errors were enountered while processing:
 zope
 zope-zaaplugins
E: Sub-process /usr/bin/dpkg returned an error cude (1)
A package failed to install.  Trying to recover:
Setting up zope (2.6.4-1.8) . . .
/var/lib/dpkg/info/zope.config: 96: arith: syntax error: "TRIES++"
dpkg: error processing zope (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of zope-zaapluins:
 sope-zaaplugins depends on zope2.7 ! zope (>= 2.6); however:
  Package zope2.7 is not installed.
  Package zope is not configured yet.
dpkg: error processing zope-zaaplugins (--configure):
 dependency problems - leaving unconfigured

---

### Post by st33med on 2007-08-15
```
sudo apt-get install zope2.7 zope
```

Do that in the terminal.

---

### Post by Evelyn on 2007-08-15
I've tried to load the zope-zaaplugins and that said to load zope 2.7.  I cannot load this without first loading python2.3 and python2.3-xml.  Loading python2.3 will unload lots of programs that I have.  What should I do?

---

### Post by st33med on 2007-08-15
Do you mean load as install?

---

### Post by EXCiD3 on 2007-08-15
try this:
```
sudo apt-get install -f
```

This will take care of installing any dependencies needed. It appears that zope has a dependency that hasn't been installed right. After you run this, try reinstalling zope again.

This is just and idea, I'm not for sure if this will work or not, but it can't hurt to try ;)

---

### Post by Evelyn on 2007-08-15
This is what happens.  There still seems to be a problem

rie-rie@dell:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up zope (2.6.4-1.8) ...
/var/lib/dpkg/info/zope.config: 96: arith: syntax error: "TRIES++"
dpkg: error processing zope (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of zope-zaaplugins:
 zope-zaaplugins depends on zope2.7 | zope (>= 2.6); however:
  Package zope2.7 is not installed.
  Package zope is not configured yet.
dpkg: error processing zope-zaaplugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zope
 zope-zaaplugins
E: Sub-process /usr/bin/dpkg returned an error code (1)
rie-rie@dell:~$

---

### Post by EXCiD3 on 2007-08-15
ok, so that wasnt the problem then.

First try "Fix broken packages" in Synaptic from the menu and see what it does. It might fix it, it might not.
If that doesnt work then in Synaptic search for Zope and Right-click zope and zope2.7 and choose "completely remove". Apply the changes and try installing the two packages again.

---

### Post by Evelyn on 2007-08-15
zope2.7 still depends on python2.3 and python2.3-xml to be installed first.  When I mark these for installation they require removeal of several (if not all) the programs that are currently installed and some which are critical to running ubuntu.  Help!

---

### Post by mali2297 on 2007-08-15
About copy/paste,

in Linux you can copy by just marking the text, then move to the place where you want to paste and middle-click.

(Perhaps not your main concern right now but anyhow.)

---

### Post by EXCiD3 on 2007-08-15
is python2.3 not installed already? you can just try completely remove on zope and zope2.7

did fix broken packages do anything?

---

