---
title: "Strange error at bootup"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-05-21
ok so my comp has been crashing recently, or rather just using the entire cpu.

at boot up im getting an error ive never seen,

```
*Starting wifi radar daemon...
Adding a multicast route for the WMA firmware loader.
SIOCADDRT: No such device.
eth0: error fetching interface information: Device not found.
Starting the WMA firmware loader.
Unable to start WMA firmware loader - Image file
"uslr/lib/wmaloader/squishguava"
listed in /etc/default/wmaloader does not exist
```

ok i search all over google for many parts of this error and got nothing

not sure it has anything to do with my cpu leaks

would appreciate any help.

this is my system

Feisty
700mhz cpu
380 mb ram
wireless dsl internet

Thx.

---

### Post by RomeReactor on 2007-05-21
Hi. It looks like there's an entry in a file (**/etc/default/wmaloader**) that should read "usr/lib/wmaloader/squishguava", but instead, due to a typo, it is unable to be located:
> *Starting wifi radar daemon...
Adding a multicast route for the WMA firmware loader.
SIOCADDRT: No such device.
eth0: error fetching interface information: Device not found.
Starting the WMA firmware loader.
Unable to start WMA firmware loader - Image file
**"uslr/lib/wmaloader/squishguava"**
listed in /etc/default/wmaloader does not exist
notice the "l" in "usr" in bold; to edit that file, open a terminal and enter:
```
gksudo gedit /etc/default/wmaloader
```
look for that line (if the file is too long to look for it at a glance, press **CTRL+F** and enter **uslr** to go to that line) and remove the offending letter. Save the file, close Gedit and reboot.

---

### Post by MkfIbK7a on 2007-05-22
> **RomeReactor said:**
> Hi. It looks like there's an entry in a file (**/etc/default/wmaloader**) that should read "usr/lib/wmaloader/squishguava", but instead, due to a typo, it is unable to be located:

notice the "l" in "usr" in bold; to edit that file, open a terminal and enter:
```
gksudo gedit /etc/default/wmaloader
```
look for that line (if the file is too long to look for it at a glance, press **CTRL+F** and enter **uslr** to go to that line) and remove the offending letter. Save the file, close Gedit and reboot.


LOL

thx i didnt notice that l!

otherwise i woulve had no problems :)

thx again

---

