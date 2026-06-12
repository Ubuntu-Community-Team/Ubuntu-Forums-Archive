---
title: "Firestarter Problem"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-03-16
Firestarter use to start at boot up but I was having problems with HOTMAIL hanging up and I removed Firestarter from the panel. I also checked IPV6 and it is set to TRUE.

When I look at the apps at startup,  firestarter is in the list. any ideas ?

 Now when I start firestarter I get the following message
```

[B]kent@GPS-3:~$ sudo firestarter
iptables v1.3.1: host/network `doubleclick.net' not found
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.1: host/network `ad.doubleclick.net' not found
Try `iptables -h' or 'iptables --help' for more information.
Firewall started
[/B]
```

Also what does **doubleclick.net** have to do with iptables ?

---

### Post by Mustard on 2006-03-16
I'm not sure what's going on, but I am just curious whether you have edited you /etc/hosts file at all.

---

### Post by kent41 on 2006-03-16
No I have not changed anything. That is what's troubling.

This is my hosts file

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
kent@GPS-3:~$

---

