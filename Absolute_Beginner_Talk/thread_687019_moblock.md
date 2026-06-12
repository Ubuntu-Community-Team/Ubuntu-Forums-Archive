---
title: "moblock"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-03
what version of moblock should I use?  .9 doesn't seem to have a gui and it blocks everything I cant even get internet.

Tips\help

---

### Post by obscur156 on 2008-02-04
If you want to use an ip filter for P2P,you can try Ktorrent and Deluge.They both have an ip filter built in.

For moblock,i have no idea.
Regards.

---

### Post by jre on 2008-02-04
Have a look at moblock-deb.sourceforge.net and [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)
The new GUI mobloquer is (partly, but under development!) already working with moblock 0.9.
For the problems with "no internet": These are the same with 0.8 and 0.9. You have to whitelist at least the IP range of your local network (LAN) and either the ports 80 and 443 or the IPs of some/many webpages. You can do this whitelisting in /etc/moblock/moblock.conf

---

