---
title: "dhcdbd.conf points to redhat"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Dazed_75 on 2008-03-03
While helping another user with a problem I noticed something strange in her message log.  Upon checking several other machines with ubuntu 7.10 I find they all have the same thing happening.  Although everything seems to be working. all machines show lines like the following in the message log:

```
Jan 21 10:28:19 lapdog2 dhcdbd: Started up. 
Jan 21 10:32:32 lapdog2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason 
Jan 21 10:33:17 lapdog2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason 
Jan 21 10:33:29 lapdog2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain 
Jan 21 10:33:29 lapdog2 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers 


```

The obvious issue related to the reference to redhat and a file system location that does not exist on an ubuntu system.  This seems to be a result of the content of /etc/dbus-1/system.d/dhcdbd.conf which DOES exist in the file system under ubuntu and contains:

```
<!DOCTYPE busconfig PUBLIC "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
    <servicedir>/usr/share/dbus-1/services</servicedir>
    <policy user="root">
        <allow own="com.redhat.dhcp"/>
        <allow send_interface="com.redhat.dhcp"/>
        <allow send_destination="com.redhat.dhcp"/>
    </policy>
    <policy context="default">
        <deny own="com.redhat.dhcp"/>
        <deny send_destination="com.redhat.dhcp"/>
        <deny send_interface="com.redhat.dhcp"/>
    </policy>    
</busconfig>
```

My 2 separate questions are:
[LIST=1]

[*]What is this configuration trying to do?
[*]Who needs to be told about it so it can be fixed for the future?
[/LIST]

---

### Post by gerben1 on 2008-05-21
anybody?

---

