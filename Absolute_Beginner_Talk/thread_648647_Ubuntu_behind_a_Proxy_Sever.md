---
title: "Ubuntu behind a Proxy Sever"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by batwings on 2007-12-23
Hi all,

  I've installed Ubuntu at my work place and our network uses a proxy server to get to the internet.

  I've no problems going to the net via the proxy server and my password, but I can't get the Add/Remove program to work.  I keep getting the "You need a working internet connection" message.

  Tried the following [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html) but still no success.  

  Appreciate any help here.  Thanks and merry x'mas :)

---

### Post by wormser on 2007-12-23
Have you tried System> Preferences> Network Proxy?  It looks like what you want but I have never used it.

---

### Post by nunnst on 2007-12-23
I had the same problem as well.  What solved it for me was setting up static DNS addresses in my router.

Another solution is to disable ipv6 in ubunto config files as well as firefox. Search the posts for ipv6 and you should find more detail on this.   However, once I set static DNS the ipv6 disable was not longer needed, and I would rather have it enabled.

Good Luck!

---

### Post by chewearn on 2007-12-23
Add/remove program uses Synaptic to manage the installation (for some reasons, Synaptic has its own place for proxy settings.)
You need to set the proxy settings in Synaptic.

Top Panel Menu > System > Administration > Synaptic Package Manager
then,
Menu > Preferences > Network

---

### Post by batwings on 2007-12-24
tried all of the above, nothing works... :(

---

### Post by batwings on 2007-12-25
any more suggestions anyone ?

---

