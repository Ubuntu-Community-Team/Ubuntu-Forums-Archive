---
title: "/etc/hosts"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by wakeboarder on 2007-09-13
Can someone explain why I had to change my /etc/hosts file from this (a pure 7.04 install)

127.0.0.1 localhost
127.0.1.1 peterk03

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


to this

127.0.0.1 localhost peterk03
#127.0.1.1 peterk03

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

to get some of my networking apps to run?
:confused:

---

### Post by tszanon on 2007-09-13
> **wakeboarder said:**
> Can someone explain why I had to change my /etc/hosts file from this (a pure 7.04 install)

127.0.0.1 localhost
127.0.1.1 peterk03

to this

127.0.0.1 localhost peterk03
#127.0.1.1 peterk03

to get some of my networking apps to run?
:confused:
I have no idea why the hosts file had that second line. Assuming that peterk03 is the name of the machine, the correct IP address that should be "assigned" to it really is 127.0.0.1.

---

### Post by ckempo on 2007-09-13
There were threads about this a while back, apparently the new method (address, localhost, name all on one line) works differently and *apparently* offers a speed boost.  But I've no idea why.

---

### Post by ravenwere on 2007-09-13
[http://ubuntuforums.org/showthread.php?t=388765](http://ubuntuforums.org/showthread.php?t=388765)

see above

---

