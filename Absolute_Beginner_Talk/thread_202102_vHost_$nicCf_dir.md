---
title: "vHost $nicCf dir?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Grukti on 2006-06-22
Got very simple problem.. i need know where is that $nicCf = "dir" is. if "$nicCf = "/etc/sysconfig/network-scripts";" that is for redhat operating systyms what it is for ubunta/kubunta/debian operating systems.... tried search this dir locations in google with no luck/helpful sites also checked vhost manuals([http://chaogic.com/vhost/documents ]("http://chaogic.com/vhost/documents")... ](*,) ](*,) 

/etc/vhost.d/V01network file
```

### ip alias configuration file or directory.  for redhat linux and similar
#   systems, set this to the network configuration directory which contains
#   configuration files for all network interfaces.  for other systems, set
#   this to a system startup script which will be used to maintain ip alias
#   configurations.
#   $nicCf = "/etc/sysconfig/network-scripts";  #redhat-style
#   $nicCf = "/etc/rc.local";                   #others
**$nicCf = "/etc/sysconfig/network-scripts";**

```

---

