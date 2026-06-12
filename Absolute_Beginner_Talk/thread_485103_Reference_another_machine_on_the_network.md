---
title: "Reference another machine on the network"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-06-26
I have two machines on a network, and they should be all set to see each other using an internal IP of 192.168.0.1

How would I use this IP to move a file from one machine to this one?

---

### Post by lamalex on 2007-06-26
you could use scp, if the receiving machine has ssh server installed (if not do apt-get install ssh-server).
then to move the file
from sending machine:
```

scp <filename> <username>@ip-of-other-machine:/path/where/you/want/the/file

```

---

### Post by phr0ze on 2007-06-26
> **Jhorra said:**
> I have two machines on a network, and they should be all set to see each other using an internal IP of 192.168.0.1

How would I use this IP to move a file from one machine to this one?

I assume you mean the gateway/router has an IP of 192.168.0.1. 
Your machines will have thier own IP. Most places where you can refer to a machine name or network location, you can use the target machine IP.

---

### Post by lazyart on 2007-06-26
> **Jhorra said:**
> I have two machines on a network, and they should be all set to see each other using an internal IP of 192.168.0.1

How would I use this IP to move a file from one machine to this one?

Machines need to have unique IP addresses.  It's kinda like naming all of your children Jesse.  You could leave a note for Jesse to do the dishes, but it'll never get done because no one can tell which one you are referring to.

---

