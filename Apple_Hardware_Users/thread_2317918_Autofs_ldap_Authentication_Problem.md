---
title: "Autofs ldap Authentication Problem"
date: 2016-03-21
forum: Apple Hardware Users
---

### Post by rameo on 2016-03-21
Hi,
    We have OSX server for samba file sharing and ldap, and we're using Ubuntu as a client for that, now I am able to mount samba and login to ldap, but I want to mount home directory remotely from server, also I sort this out and I am able to mount it, but there's another issue, I have to put username & password in the config /etc/auto.misc aside with ldap uid. 

My conclusion is after autofs consults /etc/auto.master it will be directed to /etc/auto.misc, but if there's no user,password in options in /etc/auto.misc it will not read in another place, I installed ldap-autofs and configured my ldap-uri and login works with GUI and ssh, but to mount home remotely I have to add username password.

Is there anyway to authenticate autofs to ldap without checking auto.misc? I need auto.misc to be mounting info only for the service.

---

### Post by rameo on 2016-03-22
should I move the thread to another section?

---

