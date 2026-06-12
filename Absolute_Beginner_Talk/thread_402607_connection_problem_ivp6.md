---
title: "connection problem ivp6"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by lachmac on 2007-04-06
hi1 having problem connecting to internet. on win xp i used ivp6 uninstaller to allow connection to net. ifconfig in ubuntu shows i have same additional lines in ip address.what is the equivalent to    ivp6 uninstaller i used to get win xp on the net. also where is the ivp6 coming from in the system. thank you lachmac

---

### Post by Maestro23 on 2007-04-06
Check here: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by lachmac on 2007-04-06
thak you. lachmac

---

### Post by outofnicks on 2007-04-06
You might try editing /etc/hosts, and commenting out the six lines referring to IPv6 capable hosts. It made a noticeable difference for me.

```
# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```

---

