---
title: "need help"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by bhatia_dj on 2008-01-18
i tried to install amarok music player with synaptic
it asked for the user password..this is what it showed after i entered it..


Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '-o' 'Synaptic::closeZvt=true' '--parent-window-id' '46137347' '--set-selections-file' '/tmp/tmpUMa5F-' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

any solutions?

---

### Post by lswest on 2008-01-18
you don't need to run amarok as a root user, just running it with ```
amarok
``` should be fine.

---

### Post by bhatia_dj on 2008-01-18
amarok is not installed on my system.

---

### Post by kellemes on 2008-01-18
> **lswest said:**
> you don't need to run amarok as a root user, just running it with ```
amarok
``` should be fine.

He wants to install it..

Boot into recovery mode so you're logged in as root.. then type:
```
adduser username admin
```username should be your username obviously. ;-)

This will give "username" back it's sudo priviliges.

---

### Post by bhatia_dj on 2008-01-18
great! its installing
thanks :)

---

