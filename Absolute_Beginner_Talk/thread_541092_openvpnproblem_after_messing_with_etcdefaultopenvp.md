---
title: "openvpn:problem after messing with /etc/default/openvpn"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by skivikko on 2007-09-02
Hi,

I messed up with /etc/default/openvpn, when I replaced what was in the file with "the .conf that should have linked it up with my university". So now, I replaced that with what I found from the "openvpn.howto"-internetsite (I thought that was what was there) Yes I know, im stupid, but could some one post, whats in the file /etc/default/openvpn. 

When I try to re-install tru synaptic it says

 E: openvpn: aliprosessi post-installation script palautti virhetilakoodin 127

That because im from finland "subprocess pos installation script returned error code 127"

Anyone have any ideas?

:)

-S

---

### Post by steve.horsley on 2007-09-02
These are the contents of /etc/default/openvpn. I notice that everything is commented out, so it really does nothing until you modify it.

Don't know what the error with the installer is, unless your replacement is read-only.

```
# This is the configuration file for /etc/init.d/openvpn

#
# Start only these VPNs automatically via init script.
# Allowed values are "all", "none" or space separated list of
# names of the VPNs. If empty, "all" is assumed.
#
#AUTOSTART="all"
#AUTOSTART="none"
#AUTOSTART="home office"
#
# Refresh interval (in seconds) of default status files
# located in /var/run/openvpn.$NAME.status
# Defaults to 10, 0 disables status file generation
#
#STATUSREFRESH=10
#STATUSREFRESH=0
```

---

### Post by skivikko on 2007-09-02
thanks, that did it. works!

-S

---

