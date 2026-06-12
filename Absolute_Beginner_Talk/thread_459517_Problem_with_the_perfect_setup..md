---
title: "Problem with the perfect setup."
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by tipalm73 on 2007-05-30
I am following this setup [http://www.howtoforge.com/perfect_setup_ubuntu704_p4](http://www.howtoforge.com/perfect_setup_ubuntu704_p4). With ISPConfig.

In the services it says that bind is not running and sure enough if I maunally start in the shell and it fails!

Here is the msg from the syslog:
```
May 30 19:11:45 tipalm named[5588]: starting BIND 9.3.4 -u bind -t /var/lib/named
May 30 19:11:45 tipalm named[5588]: found 1 CPU, using 1 worker thread
May 30 19:11:45 tipalm named[5588]: loading configuration from '/etc/bind/named.conf'
May 30 19:11:45 tipalm named[5588]: listening on IPv4 interface lo, 127.0.0.1#53
May 30 19:11:45 tipalm named[5588]: listening on IPv4 interface eth0, 192.168.1.101#53
May 30 19:11:45 tipalm named[5588]: loading configuration: empty label
May 30 19:11:45 tipalm named[5588]: exiting (due to fatal error)

```

If you need any config files you only need to ask.

HELP!

Thanks in advance

---

