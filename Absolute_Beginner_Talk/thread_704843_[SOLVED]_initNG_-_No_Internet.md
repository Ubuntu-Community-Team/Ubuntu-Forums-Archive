---
title: "[SOLVED] initNG - No Internet"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-02-22
Ive just installed InitNG because people say its faster.

im happy to use InitNG

i follwed this: [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG) 
to install InitNG and configure it, very helpful :)

but i have no internet when i use it :(

i tried sudo /etc/init.d/network restart and this was the output

```
 scott@scott-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
                                                                         [fail]
scott@scott-desktop:~$ 
Message from syslogd@localhost at Sat Feb 23 00:11:12 2008 ...
localhost InitNG: "/tmp/buildd/initng-0.6.7/plugins/daemon/initng_daemon.c", kill_daemon() #973 FAIL: Trying to kill a service (daemon/dhcdbd) with a pid (4355), but there exists no process with this pid! 


```

Any ideas?

---

### Post by PeterJS on 2008-02-22
Have you tried creating /var/run/network/ifstate?

Here's what I've got:
```

peter@Osirus:~$ cat /var/run/network/ifstate 
lo=lo

```
Which makes no sense, as I've also got my wireless up (how else would I be online to post this), but see if creating that file makes it happy.

---

### Post by skymera on 2008-02-22
actually after playing around a bit and few restarts i see no speed benefits =\

so im going to uninstall, thanks anyway! =D

---

