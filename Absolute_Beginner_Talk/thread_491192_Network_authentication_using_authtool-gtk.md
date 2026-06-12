---
title: "Network authentication using authtool-gtk"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by caffienefree on 2007-07-03
Hello,

I'm trying to connect to a windows domain using authtool-gtk. It loads, I select Active Directory Authentication. These are my settings (changed the names for protection):

> Kerberos TGT Server:
Password Server:
Default Realm:
Admin Server:
Domain/Workgroup: domainname.site.org
AD Realm: server.org
Administrator: administrator
User ID Map: 10000-20000
AD Server: servername.site.org
Admin password: *******
Group ID map: 10000-20000

I issue the command wbinfo -u and receive an "Error looking up domain users". Any ideas? Am I misconfiguring something?

---

