---
title: "line 59 error in update manager"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by hps on 2007-12-02
When I tried to update my system package manager I get the following error.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 59 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Any ideas as to what I have corrupted

---

### Post by GSF1200S on 2007-12-02
> **hps said:**
> When I tried to update my system package manager I get the following error.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 59 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Any ideas as to what I have corrupted

Please post the contents of /etc/apt/sources.list

To do this, type:

sudo gedit /etc/apt/sources.list

and copy it all into a reply :)

Do you have any custom sources added to apt, or a third party sources.list?

---

