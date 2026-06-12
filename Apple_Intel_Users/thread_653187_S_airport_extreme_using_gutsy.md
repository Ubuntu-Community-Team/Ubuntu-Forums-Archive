---
title: ":S airport extreme using gutsy"
date: 2007-12-29
forum: Apple Intel Users
---

### Post by alpinesatan on 2007-12-29
Hey people.

Firstly sorry in advance, i know there are loads of these posts but none seem to work sadly.
I have ubuntu 7.10 setup as dual boot using rEFIt and id love airport to work.
I have tried for a few days now and no luck.
Its a AR5418 802.11a/b/g/n Wireless PCI Express Adapter in an itel based macbook.
if anyone has got this working id love you to post what you did.

Kind Regards

---

### Post by ditsch on 2007-12-29
I got it to work with the SVN snapshot using this commands:

```
sudo apt-get install build-essential subversion
svn checkout http://svn.madwifi.org/trunk madwifi
cd madwifi
make
sudo make install
sudo modprobe ath_pci
```

Sometimes I get [this bug]("http://madwifi.org/ticket/1017"), but it is better than nothing.

---

### Post by alpinesatan on 2007-12-29
yep, ive tried this.

mikal@mikal-laptop:~$ sudo apt-get install build-essential subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate

still trying to sort it out

---

### Post by ditsch on 2007-12-29
This seems to be a problem with your sources.list.

---

### Post by alpinesatan on 2007-12-29
quite possibly :D
ive got it working now :guitar: i downloaded and installed everything manually, went to the madwifi directory, then followed the rest of the commands,
make
sudo make install
sudo modprobe ath_pci

Thanks again for your help, please note ive given you thanks for the posts :D

Happy New Year

---

