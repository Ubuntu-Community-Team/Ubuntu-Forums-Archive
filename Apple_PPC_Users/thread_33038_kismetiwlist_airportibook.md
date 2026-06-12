---
title: "kismet/iwlist airport/ibook"
date: 2005-05-09
forum: Apple PPC Users
---

### Post by zenlunatic on 2005-05-09
Here is my error message:

```
zenlunatic@ubuntu:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (ciscosource): Enabling monitor mode for cisco source interface eth0 channel 6...
FATAL: Unable to open cisco control file '/proc/driver/aironet/eth0/Config' 2:No such file or directory
```

Does kismet work with airport?

Secondly.

```
zenlunatic@ubuntu:~$ iwlist eth1 scan
eth1      Failed to read scan data : Operation not supported
```

Does airport driver not support iwlist scanning? How am I to find wireless networks with no kismet or iwlist scanning? Thanks.

---

### Post by zenlunatic on 2005-05-09
Okay I see in another thread that only the CVS version of airport drivers support iwlist scan. Is that correct?

---

### Post by khc on 2005-05-10
Yes

---

