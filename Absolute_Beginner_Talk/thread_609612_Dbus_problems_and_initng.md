---
title: "Dbus problems and initng"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-11
ok, yesterday i switched to initng following a tut on ubuntu wiki.

it was all fine, but when i login and ready i get a system beep and a terminal pops up and says

```
 scott@scott-desktop:~$ 
Message from syslogd@localhost at Sun Nov 11 12:05:58 2007 ...
localhost InitNG: "/tmp/buildd/initng-0.6.7/plugins/daemon/initng_daemon.c", timeout_DAEMON_WAIT_FOR_PID_FILE() #765 FAIL: Service "daemon/dhcdbd" wait for pidfile timed out! Will kill daemon now. 

Message from syslogd@localhost at Sun Nov 11 12:05:58 2007 ...
localhost InitNG: "/tmp/buildd/initng-0.6.7/plugins/daemon/initng_daemon.c", kill_daemon() #973 FAIL: Trying to kill a service (daemon/dhcdbd) with a pid (5739), but there exists no process with this pid! 

```

those also hang 15 seconds at shutdown :(

also i dont think dbus is starting properly, attached is a screenshot of my services and network-admin.

they only appear if i run

```
 sudo /etc/init.d/dbus restart 
```

can someone help?
ive been googling for hours

thank you thank you :)

---

### Post by skymera on 2007-11-11
thoughts?

---

