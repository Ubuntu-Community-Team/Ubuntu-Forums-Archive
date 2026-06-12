---
title: "[SOLVED] HOW-TO connect from one ubuntu to a virtualized ubuntu in parallels with ssh"
date: 2008-07-20
forum: Apple Hardware Users
---

### Post by herrmeier on 2008-07-20
I want to connect from one ubuntu 192.168.3.1 to another ubuntu which is running on a virtual machine in parallels on a newly updated just bought mac mini.
The mac-mini therefore has two IP-Adresses:
1. 192.168.3.2 is leopards IP
and
2. 10.211.55.3 ist the ip-adress of the newly added ip-adress of parallels.

I can connect from ubuntu locally without any problem with:
```
$ ssh -C -X user@localhost
```

it also worked from the termin-program in macOS.
```
$ ssh -C -X user@10.211.55.3
```

what didn't work though was connecting from one ubuntu on the other pc at ip 192.168.3.1 to the virtual ubunto on the mac mini.
```
$ ssh -C -X user@10.211.55.3
```

Like it should connecting to the real IP 192.168.3.2 only connected to the mac os worked just fine, but I still couldn't connect to the virtually running ubuntu.
```
$ ssh -C -X user@192.168.3.2
```

What am I forgetting? What can I do to connect to the virtualised ubuntu?
Thanks a lot already for having read all this.
Please don't hesitate to give me some input.

Yours, HM


PROBLEM SOLVED:
You just have to switch from shared networking to bridged networking.:)

---

### Post by cyberdork33 on 2008-07-21
> **herrmeier said:**
> PROBLEM SOLVED:
You just have to switch from shared networking to bridged networking.:)

Yep, that is exactly it. 

Please mark this thread as solved (Thread Tools Menu).

---

