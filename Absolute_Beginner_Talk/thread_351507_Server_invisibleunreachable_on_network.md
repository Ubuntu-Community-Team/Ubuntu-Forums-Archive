---
title: "Server invisible/unreachable on network"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Pocket Aces on 2007-02-02
This has got to be a simple fix but I just can't solve it.  Basically a fresh ubuntu install, put vsftpd on and I think thats about the only extra package.  vsftpd works fine using 127.xxx and on my local network 192.168.xxx from the machine itself.  From other local network computers however the ftp server cannot be connected to.  Pings are also ignored as is ssh.  I ran a quick portscan and not a single port appears open (I expected ftp and ssh ports to appear).

I haven't installed any firewalls or done anything with iptables.  There must be something out of the box which is blocking incoming connections but I can't find it.

Thanks,
pa

---

### Post by psyne on 2007-02-02
Crazy question but are on a NATed connection behind a broadband firewall?

---

### Post by Pocket Aces on 2007-02-02
Computers are connected by a standard linksys router, no firewall, local network computers should have full access to each other.

---

