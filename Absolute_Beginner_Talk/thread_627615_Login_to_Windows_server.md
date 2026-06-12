---
title: "Login to Windows server"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by rsamanya on 2007-11-30
I just installed feisty. Is there a way to have ubuntu login page to login into my Windows 2000 server? This way I don't need to add each and every user on the network.

In WinXP this is pretty simple, as I just need to fill in the domain.

---

### Post by sixsixone on 2007-12-01
You can use your existing Windows user names & passwords to log into samba shares- it'll ask you for the optional domain parameter.

It's not so simple to share the same details at login though. If you're maintaining a large number of machines on both OSes then some kind of LDAP / ActiveDirectory service would partially solve the problem as they could store the user credentials in the same place.

Anyone have any more elegant solutions?

---

