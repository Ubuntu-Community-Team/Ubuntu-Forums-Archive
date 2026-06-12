---
title: "Apache on my vmware partition"
date: 2011-04-13
forum: Apple Hardware Users
---

### Post by vanhornd on 2011-04-13
Hello,

I'm trying to get Apache running on my Ubuntu partition of my IMac (vmware is my partition tool). When I say this as a normal user in a terminal:  apachectl start
I get this response:  (13) permission denied:  make sock:  could not bind to address 192.168.1.107:80
No listening sockets available, shutting down
Unable to open logs
Action 'start' failed

When I say this: sudo apachectl start
I get this response:  #98 Address already in use: make sock: could not bind to address [ : : ]:80
                                   #98 Address already in use: make sock: could not bind to address 0.0.0.0:80
No listening sockets etc. (same as above)

By the way this is a first time installation of Apache on this machine.

Could anybody suggest a cure.  Thank you.

---

