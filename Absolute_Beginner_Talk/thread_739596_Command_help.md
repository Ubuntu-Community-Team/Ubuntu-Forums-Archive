---
title: "Command help"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by reviveL on 2008-03-29
I recently ran into the trouble of having to type in the following command in Terminal.

dpkg --configure -a

I'm just curious what this command is doing.

Any help is appreciated. Thanks.

---

### Post by jken146 on 2008-03-29
[quote=man dpkg] dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package. If -a or --pending is given instead of package, all  unpacked  but
              unconfigured packages are configured.

              Configuring consists of the following steps:

              1.  Unpack  the  configuration  files, and at the same time back up the old configuration files, so
              that they can be restored if something goes wrong.

              2. Run postinst script, if provided by the package.[/quote]

Does that make sense?

---

### Post by reviveL on 2008-03-30
My guess would be that all those commands running are installing the updates and backing them up. Also when I run this command and waiting for it to configure my computer locks up and I can't move the mouse or type.

---

