---
title: "gnome errors!!!!!"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by daberger on 2008-03-30
when i boot up i get this message

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.



indeed, it does stop my themes and sounds from working. i cannot start the gnome-settings daemon (system>preferences> appearance) but i can still activate desktop effects by running
```
SKIP_CHECKS=yes compiz
```
and i also get weird lines coming down my desktop.

i am running hardy just in case that might have anything to do with this problem. i think another thing it might have to do with is that i recently modified my xgl file (see the thread desktop effects cannot be enabled)

---

### Post by chewearn on 2008-03-30
It's a known bug; check the bug report here for some clues:
[https://bugs.launchpad.net/ubuntu/+bug/197759](https://bugs.launchpad.net/ubuntu/+bug/197759)

---

