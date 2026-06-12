---
title: "Macbook 1,1 hibernation drains the battery"
date: 2009-08-04
forum: Apple Hardware Users
---

### Post by sasepp on 2009-08-04
Hi all,

when I hibernate my Macbook 1,1 on Jaunty (with latest updates) my battery drains out in a few days. For suspend to RAM this makes sense, but not for hibernation. I have not modified any suspend/hibernation settings. I'm assuming my Macbook uses dbus-pm method for hibernation (see /etc/default/acpi-support):

```

SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"

```

Anyways, I've had several other Linux flavors on this laptop and none of them has had this issue with hibernation. This is very annoying as it renders hibernation effectively useless. I'd rather not build a custom kernel unless that's unavoidable.

Any ideas how to fix this?

---

