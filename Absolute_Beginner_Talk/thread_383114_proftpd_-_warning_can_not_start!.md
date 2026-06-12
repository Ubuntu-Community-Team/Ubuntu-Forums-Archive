---
title: "proftpd - warning can not start!"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-03-12
Hi,

I have installed proftpd, as per a "how-to" setup an ftp server thread that i found on these forums, but i have had no luck starting up the server.

When i type in
```
sudo /etc/init.d/proftpd start
```
i get a warnign
```
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
```

I cant for the life of me work out why it isn't working. Can someone shead some light on what i am doing wrong?

---

### Post by stealth17 on 2007-03-13
> **LoicNyssen said:**
> Hi,

I have installed proftpd, as per a "how-to" setup an ftp server thread that i found on these forums, but i have had no luck starting up the server.

When i type in
```
sudo /etc/init.d/proftpd start
```i get a warnign
```
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
```I cant for the life of me work out why it isn't working. Can someone shead some light on what i am doing wrong?

heh, I just got the same problem when I installed 5 minutes ago. Please help someone :(

**EDIT:** Seems it only works in standalone. Change the proftp config file to standalone and it will start right up.

---

### Post by poiiop on 2007-12-30
Same problem here ... 

I changed inetd to standalone in proftpd.conf 

...              
...
ServerName                      "ubuntu710"
ServerType                      **standalone**
DeferWelcome                    off
...
...

and added the hostname (bold ubuntu710 in this ex) in /etc/hosts

...
...
127.0.0.1       localhost
127.0.1.1       ubuntu710
10.0.0.100      ubuntu710

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback **ubuntu710**
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
...
...

/etc/init.d/proftpd start

Now the ProFTPd starts.

Any hints about starting under init.d instead of standalone ??

---

