---
title: "Squid Doesnt work"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-04-15
I get this error:
```
ben@Ben-Ubuntu:~$ squid
FATAL: Unable to open configuration file: /etc/squid/squid.conf: (13) Permission denied
Squid Cache (Version 2.6.STABLE5): Terminated abnormally.
CPU Usage: 0.004 seconds = 0.000 user + 0.004 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
ben@Ben-Ubuntu:~$ 

```
What does this mean and how do i make squid work?

---

### Post by speeves on 2007-04-15
You are trying to start squid as the "ben" user, but "ben" doesn't have rights to start it.  I would start it like:

sudo /etc/init.d/squid start

That will start squid as root, giving it access to the ports and sockets that it needs.

Good luck!

---

### Post by ProjectWhat on 2007-04-15
actually i found a webpage online on how to configure squid once i done that it worked. I even had some people test it remotely.

---

