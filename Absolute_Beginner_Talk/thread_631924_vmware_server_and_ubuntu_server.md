---
title: "vmware server and ubuntu server"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2007-12-04
I have installed ubuntu-server edition in vmware server. it's a NAT networking. I'm trying to make the ssh server to be accessible via the internet, like *****.myvnc.com

I'm behind a router.

Thanks in advance.

---

### Post by wormser on 2007-12-04
There are guides to open ports on most routers at [PortForward.com]("http://portforward.com/routers.htm")  You will need to open up port 22 for ssh.  [DynDNS]("http://www.dyndns.com/") has a free service to set up a domain like you want.  Then make sure that Ubuntu has sshd installed and port 22 is open.

__________________
Proud to be a [COLOR="Red"]Agnostic[/COLOR]! Knowledge is my savior.

---

### Post by LookTJ on 2007-12-04
I don't have a problem with opening ports on the host os, but on the guest os.

---

### Post by LookTJ on 2007-12-05
bump to first page.

---

