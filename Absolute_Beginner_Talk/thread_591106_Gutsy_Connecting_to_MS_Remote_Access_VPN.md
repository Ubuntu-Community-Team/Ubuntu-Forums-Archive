---
title: "Gutsy: Connecting to MS Remote Access VPN"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2007-10-25
I need to connect to a Routing and Remote Access server on a Windows 2003 box at my work.  I trolled the forums and found instructions relating to Edgy/Feisty which I started out trying for Gutsy.  I  tried to install the network-manager app and aptitude coudn't find it.  So I read somewhere to try to pptp-linux package which did install, and also installed network-manager-pptp...both of which I can find support files for, but no executables.  

I tried working off of this tutorial:

[http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)

But aptitude couldn't find a pptpconfig package, and I have all the repositories checked in Synaptic.

I'm at a loss as to what package to install...does Gutsy use something different than Edgy or Feisty for this function?

---

### Post by fain on 2007-10-25
network-manager is installed by default. it should be in the top right corner. you click on it and if you have the network-manager-pptp installed it should say "vpn connections" this will let you configure your connection. there was a bug in feisty that only let me connect in dhcp mode. hope this is fixed in gutsy.

---

