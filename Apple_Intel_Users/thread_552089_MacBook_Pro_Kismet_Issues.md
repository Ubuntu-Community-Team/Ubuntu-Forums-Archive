---
title: "MacBook Pro Kismet Issues"
date: 2007-09-16
forum: Apple Intel Users
---

### Post by tsm1723 on 2007-09-16
Hi,

I recently changed the linux installation on my MacBook Pro Core Duo (not Core 2) from Gentoo to Ubuntu 7.04. So far I've been very pleased, but I am having some trouble getting wireless sniffing working properly. I've found that when running kismet, I can see LLC packets, but not data packets. I tried downloading the latest madwifi drivers from subversion and installing them, but it didn't make any difference. I know the hardware should support passive sniffing of data packets because it was working under Gentoo with madwifi drivers, but I can't seem to get it working on my Ubuntu install. Any suggestions?

Thanks

---

### Post by tsm1723 on 2007-09-16
Nevermind - I've found a solution. It turns out that the older madwifi drivers at [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz) work correctly.

---

