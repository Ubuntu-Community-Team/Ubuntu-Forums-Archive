---
title: "DNS not being kept"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by CurlyBlue on 2006-09-04
hi All

Got a problem. Running 6.06 and its conected to a LAN - I put the DNS addresses into the network settings and can connect to the LAN and the Internet with no issues.

However when I restart the machine into Linux the DNS settings have gone!

any ideas peeps?

Thx

CurlyBlue

---

### Post by Uluen on 2006-09-04
Are you using the network applet? It's behaving rather odd here so I don't use it. You are using fixed IP I guess?
```
$ cat /etc/resolv.conf
```
The format is ```
nameserver xxx.xxx.xxx.xxx
```

---

### Post by CurlyBlue on 2006-09-04
No we are using DHCP but we have fixed DNS on our outbound server.

Its the DNS that keeps dropping.

Cheers

CurlyBlue

---

