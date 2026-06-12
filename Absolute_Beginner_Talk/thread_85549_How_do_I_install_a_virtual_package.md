---
title: "How do I install a virtual package?"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-02
#aptitude search djbdns
v djbdns

#aptitude show djbdns
Package djbdns
State Not a real package

#aptitude -r install djbdns
No candiate version found for djbdns

How should I go about installing this DNS server program (djbdns) ?

Thanks.

---

### Post by GreyFox503 on 2005-11-03
I just took a quick peek in Synaptic for "djbdns" and I got three results:

djbdns-installer
libdjbdns1
libdjbdns1-dev

The description for djbdns-installer is :  "Source only package for building djbdns"

Hope that helps.  :)

---

### Post by Akhran on 2005-11-05
In another scenerio, I have a package that requires "mail-transport-agent" to be installed. How can I find out what are the packages that will provide the virtual package?

Or yet another scenerio, I need to have a virtual package called "X11-text-viewer" to be installed and from reading some examples in the man pages for apt-cache, I get to know that only one package, "xless", provides for "X11-text-viewer". Is there any command that will let us know that the required package is "xless"?

Thanks !

PS. I did try to search for "mail-transport-agent" and "X11-text-viewer" at [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) , but there is no result returned.

[QUOTE=GreyFox503]I just took a quick peek in Synaptic for "djbdns" and I got three results:

djbdns-installer
libdjbdns1
libdjbdns1-dev

The description for djbdns-installer is :  "Source only package for building djbdns"

Hope that helps.  :)[/QUOTE]

---

### Post by GreyFox503 on 2005-11-06
Sorry, but I don't have much experience in resolving dependencies.  I'm not sure what you need to do to get those packages.

If you're installing something you find through Synaptic, it should automatically mark all dependencies and download them for you.  However, if you're trying to install software yourself (from a .deb or .tgz) then it gets a little more tricky.

---

