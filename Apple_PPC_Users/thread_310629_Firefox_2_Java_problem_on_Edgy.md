---
title: "Firefox 2 Java problem on Edgy"
date: 2006-12-01
forum: Apple PPC Users
---

### Post by funk19 on 2006-12-01
Hi guys

First post on the forum so go easy :P

I've been running ubuntu on an i386 machine and a few days ago I decided to format my ibook G4 PPC and install Edgy 6.10. All has been fine, apart from a few irritating functional items that the i386 system had and PPC doesn't support such as WINE and VMWARE.

That said I am having a bit of a problem with Java Runtime Environment (JRE) and can't seem to get it installed on my machine and therefore can not install any plugin for firefox.

I've tried to search the forums but can't seem to find anything that relates to this issue on the PPC so that's why I'm posting here.

Firstly I have my universe & multiverse activated in /etc/apt/sources.list and have tried to install JRE using both apt-get and synaptic.

apt-get gives me the following:

```
sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate

```

Similarly if I try and install sun-java5-jre via synaptic I get the following error message:

```
sun-java5-jre:
 Depends: sun-java5-bin (=1.5.0-08-0ubuntu1) but it is not installable or
 	ia32-sun-java5-bin (=1.5.0-08-0ubuntu1) but it is not installable
```

I'm really keen to get JRE installed, specifically for Firefox, so any help is appreciated.

---

### Post by APU on 2006-12-01
There is no Sun Java for PPC, at least not yet. You can get the IBM Java-5 SDK from IBMs Developer sites (you have to register, but at least it's free of charge) and install that. Just look in the Ubuntu Wiki - you'll find a howto there.

Hopefully the Sun Java will be available on any platform you can think of soon.. since they opened it just recently!

---

### Post by funk19 on 2006-12-02
Thats APU. Much appreciated!

---

