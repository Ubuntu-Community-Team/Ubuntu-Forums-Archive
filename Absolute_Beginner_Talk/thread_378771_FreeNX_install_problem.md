---
title: "FreeNX install problem"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by frenchtomytoast on 2007-03-07
I did a fresh install of FreeNX using the files off nomachine's website
When I check the status of freenx it says

NX> 900 SSH: connect to host 127.0.0.1 port 22: Connection refused
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.

Any thoughts?

----EDIT----
Did a clean install and installed openssh after freenx. Now, the connection times out when I get authenticated.

---

### Post by Child of Wonder on 2007-03-08
Seems like your firewall is stopping port 22 or you don't have ssh server installed.

---

