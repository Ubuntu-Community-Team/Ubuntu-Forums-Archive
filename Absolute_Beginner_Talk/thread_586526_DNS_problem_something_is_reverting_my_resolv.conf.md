---
title: "DNS problem: something is reverting my resolv.conf"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Grafen on 2007-10-22
...my Internet connection (adsl) works fine, but I can't use my local network connection because of this.

I've tried all of [*this methods*](https://help.ubuntu.com/community/StaticDnsWithDhcp), but my local network works only for 1-2 minutes after ```
sudo invoke-rc.d networking restart
```

Tried to lock my resolv.conf with ```
sudo chattr +i /etc/resolv.conf
``` it helps me not.

There was a solution in old themes, to comment some lines in /etc/dhcp3/dhclient-script file, but there is no such file! :(

Sorry for my bad english & stupid questions, but it's first time, when I use Linux.

---

### Post by Grafen on 2007-10-22
Solved

---

