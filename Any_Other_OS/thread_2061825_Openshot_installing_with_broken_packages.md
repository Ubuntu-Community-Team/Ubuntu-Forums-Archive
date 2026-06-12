---
title: "Openshot installing with broken packages"
date: 2012-09-23
forum: Any Other OS
---

### Post by Janiporo on 2012-09-23
I can not pinpoint the problem now, so seeking for help. Using Mint 13 (Based on Ubuntu 12.04 and btw looks totally like 10.04)

I manually updated from some repository (can not remember which, since removed it after) some files, included libmlt4 (If I remember correctly) and then all went to h*ll,

Reason I did these was Openshot was having problems with MLT, And I saw this guide which told I must update MLT manually. One package (do not remember which) wanted to uninstall kdenlive and openshot, do not know why, after that it is impossible to reinstall Openshot.

When I try to reinstall Openshot it wants to install 
--> python-mlt3
which wants to install
--> libmlt4
which wants to install
--> libmlt++3
which wants to install
-->  libmlt5
But libmlt5 wants to uninstall libmlt4.

So I am going in circles here.




Any workaround?

---

### Post by Janiporo on 2012-09-23
Seems here might be the answer, testing out.

--> [http://ubuntuforums.org/showthread.php?t=2025685](http://ubuntuforums.org/showthread.php?t=2025685)

---

### Post by Janiporo on 2012-09-23
No help there either.

This is the guide that I used to "fix" things [https://answers.launchpad.net/openshot/+faq/1861](https://answers.launchpad.net/openshot/+faq/1861)

---

### Post by Perfect Storm on 2012-09-24
Moved to Other OS/Distro Talk.

---

### Post by Janiporo on 2012-09-26
I tried AVLinux and there Openshot does not need any of those previously mentioned to run.

    In AVLinux it needs:
librsvg2-common
python-glade2
python-gtk2
mlt
python-mlt
python-pygoocanvas
python-xdg
python (>=2.5)
python-support (>=0.90.0)

---

### Post by Janiporo on 2012-09-26
In Mint it's dependencies are as following:
gtk2-engines-pixbuf
fontconfig
librsvg2-common
melt
python-gtk2
python-httplib2
python-imaging
python-mlt3 / mlt2 / mlt
python-pygoocanvas
python-xdg
python (>=2.5)
python-support (>=0.90.0)

there is no mlt... 

I do not understand what is going on. My brain tells me there should be same dependencies :rolleyes:

---

