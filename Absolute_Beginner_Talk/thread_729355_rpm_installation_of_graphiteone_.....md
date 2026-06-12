---
title: "rpm installation of graphiteone ...."
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by jtmedin on 2008-03-19
trying to install graphiteone cad
think i got it converted from rpm
then tried the following:

ted@ted-desktop:~/Desktop$ sudo apt-get install graphiteone-lib*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package graphiteone-libs-1.3-1-suse93.rpm
ted@ted-desktop:~/Desktop$ 

I have that file on my desktop so why cant it find it? TIA

---

### Post by glennric on 2008-03-19
Type 
```
sudo dpkg -i graphiteone*.deb
```

---

