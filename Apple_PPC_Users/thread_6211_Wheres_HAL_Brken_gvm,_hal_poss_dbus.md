---
title: "Wheres HAL? Brken gvm, hal poss dbus?"
date: 2004-11-26
forum: Apple PPC Users
---

### Post by incandescant on 2004-11-26
So I've had Ubuntu on my iBook since the CD's arrived from Canonical and not booted OS X once :)
It's all been very smooth except for when I tried to get Beagle installed. Not only is Beagle not working (acceptable) but the point of this post is gnome-volume-manager (gvm) has stopped playing ball and mounting my USB stick automagically.

I tried manually starting gvm but I get this error:

```
libhal.c 644 : Error connecting to system bus: Failed to connect to socket /usr/var/run/dbus/system_bus_socket: Connection refused

** (gnome-volume-manager:4451): WARNING **: manager.c/1032: failed to initialize HAL!
```

I had updated my Kernel to a patched iNotify kernel but reverting to the old Kernel doesn't help. 
I've tried running gvm as root and user and get the same error.

It looks like it could be a DBus error?

Would removing and re-installing DBus help??

I put dbus# on for Beagle, could this have broken things?

Please help. This is my only gripe with my Ubuntu set up and it's only a really small one but annoying nontheless.

Best

Incandescant

P.S: running latest gvm etc from Hoary

EDIT: This seems more of a general problem. If a mod could move it?
EDIT2: Put a copy in General Support

---

