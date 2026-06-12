---
title: "VPN/PPTP for PPC"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by thenes on 2006-06-01
As soon as my exams are over, later this month, I will try dualbooting OSX and Ubuntu. I have been running the liveCD and have not run into any problems. 

Yet, where I live, I can only connect to the internet through VPN (PPTP). I will install Ubuntu at my parents house, where this is not required, but I will need to have the software for connecting to VPN already installed as I go back home.

Is such a software already supported in the Ubuntu bundle (I cannot find it on the liveCD), or is there anywhere I can find such a software that will run on PPC?

Thanks.

---

### Post by NiN on 2006-06-01
If you need something simple to handle (but not necessary easy to set up)
you can use the pptp plugin for network manager.

Sadly it's not in the repository (like all vpn plugins for network-manager),
but you can set it up more or less easy.

Have a look at:

[http://www.ubuntuforums.org/showthread.php?t=176979](http://www.ubuntuforums.org/showthread.php?t=176979)

---

### Post by scottlpatterson on 2006-06-01
I use vpnc on i386 to connect to our CISCO box. I assume it works just as well for powerpc. I plan on verifying that in the near future on my iBook.

Here's the package info:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vpnc&searchon=names&subword=1&version=dapper&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vpnc&searchon=names&subword=1&version=dapper&release=all")

---

### Post by Biber on 2006-06-02
vpnc works just fine with my uni VPN. You need to enable multiverse I think.

---

