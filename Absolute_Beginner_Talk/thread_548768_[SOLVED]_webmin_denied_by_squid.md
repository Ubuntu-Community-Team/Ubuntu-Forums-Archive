---
title: "[SOLVED] webmin denied by squid"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-11
Hi there,

I have set up squid to run as a proxy server and all is well except I cannot access https sites on the server that squid is running on. I CAN access https sites on the internet.

I have webmin running on https and I get the following from squid when I try to access it from a client on the LAN at this address:

[https://192.168.0.6:10000/](https://192.168.0.6:10000/)

```
**The requested URL could not be retrieved**

   While trying to retrieve the URL: [192.168.0.6:10000]("https://192.168.0.6:10000/192.168.0.6:10000") 
 The following error was encountered:[LIST]
[*]  Access Denied.   Access control configuration prevents your request from being allowed at this time.  Please contact your service provider if you feel this is incorrect.[/LIST]
```I can however access my backuppc website which is at [http://192.168.0.6/backuppc](http://192.168.0.6/backuppc) with no problems.

What do I need to change in the squid.conf?

Thanks!

---

### Post by keymoo on 2007-09-12
I solved this now thanks.

---

### Post by onegreenparker on 2008-05-27
Please post the fix for this, I've hit the same problem.

---

### Post by ikt on 2008-07-09
> **keymoo said:**
> I solved this now thanks.

great way to not help anyone looking to solve the same problem.

---

