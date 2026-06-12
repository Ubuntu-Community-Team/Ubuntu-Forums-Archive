---
title: "ssh proxy server"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Drew32 on 2006-09-01
how would i go about setting up an ssh proxy server that would accept clients on port 442 and route it to port 6112-6119?
anyone got any suggestions?

---

### Post by kidders on 2006-09-03
My suggestion would be to avoid proxying SSH connections, unless there is some specific reason why you would want to. Your post makes it sound as if you have multiple computers on a LAN, all of which you would like to access externally via SSH, or something like that.

Assuming this is the case (which, of course, it may not be lol), you can always connect indirectly to each machine, through the one that *is* accessible from the www.

A better solution is **iptables**, the Linux firewall/router.

If I'm on the right track with my interpretation of your question, let me know, and I'll walk you through the setup of iptables. It would let you selectively redirect incoming connections to different computers, based on the port number.

---

