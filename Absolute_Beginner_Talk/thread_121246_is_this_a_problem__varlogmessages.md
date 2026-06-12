---
title: "is this a problem?  /var/log/messages"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by stardotstar on 2006-01-24
I am getting a lot of this and don't know what it all means:

```

wparker@geko:~$ tail /var/log/messages
Jan 25 07:05:33 localhost gconfd (wparker-8666): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jan 25 07:05:33 localhost gconfd (wparker-8666): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jan 25 07:05:33 localhost gconfd (wparker-8666): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jan 25 07:05:33 localhost gconfd (wparker-8666): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan 25 07:05:49 localhost gconfd (wparker-8666): Resolved address "xml:readwrite:/home/wparker/.gconf" to a writable configuration source at position 0
Jan 25 07:17:27 localhost exiting on signal 15
Jan 25 07:17:28 localhost syslogd 1.4.1#17ubuntu3: restart.
Jan 25 07:37:29 localhost -- MARK --
Jan 25 07:40:52 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jan 25 07:41:18 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name

``` 
eth1 is my wireless interface being driven by network manager...

---

