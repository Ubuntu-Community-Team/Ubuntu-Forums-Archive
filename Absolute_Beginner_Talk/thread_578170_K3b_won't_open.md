---
title: "K3b won't open"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by saywot on 2007-10-17
Here's a return from opening (or not as the case may be) K3b with a termina

l>  :~$ sudo k3b
Password:
Error: "/tmp/ksocket-U1HfEB" is owned by uid 1000 instead of uid 0.
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
kdeinit: DCOPServer could not be started, aborting.
ERROR: KUniqueApplication: Can't setup DCOP communication.


And I can't seem to be able to start or stop the DCOPserver

---

### Post by llamakc on 2007-10-17
Why do you need to run it with sudo?

---

### Post by saywot on 2007-10-17
Because it won't run in a user account
I thought I'd try as a super-user and it produced the same message

---

### Post by taurus on 2007-10-17
What happens if you just run

```
k3b
```

---

