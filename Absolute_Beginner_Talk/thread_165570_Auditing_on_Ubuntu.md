---
title: "Auditing on Ubuntu"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by pcnmt on 2006-04-24
I need to get an audit daemon like auditd for Ubuntu.  Has anyone tried this or knows of a similar application?

---

### Post by javahollic on 2006-09-13
I just wanted to do the same thing, to provide basic file auditing.  auditd isnt available through synaptic, but a pretty old (and apparently discontinued) version are available on various mirrors (eg [here]("http://www.mirrors.wiretapped.net/security/host-security/auditd/")).


I downloaded the latest, the source stuff builds on Dapper **except** for the kernel module.  The install stuff needs pointing to /etc/init.d not /etc/rc.d/init.d

So its basically not a straight forward install.

Not sure on any other low level audit tools other than installing SE Linux. :-k

---

### Post by javahollic on 2006-09-13
After looking at [SELinu wiki]("http://en.wikipedia.org/wiki/SELinux"), its looks like all this was merged into the 2.6 kernel, so auditd is officially dead.  Related 'se linux' Ubuntu packages are available for Dapper.  I ahvent looked further.

---

