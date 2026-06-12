---
title: "Remove &quot;configuring network inerface&quot; from startup ..."
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2006-01-28
Hi all.

I wan to remove "Configuring network interface" from startup.
It doesn't work now, and when I ctrl+c it doesn't seem to have any effect on my ability to go online (wireless) afterwards.

How can I edit the startup sequence (and where can I read about it)?

Thanks! ;) 
Steff

---

### Post by Lambert on 2006-01-29
If you want to just prevent an interface from configuring at boot open up /etc/network/interfaces file and remove any line that looks like

auto eth0

You'll need root privledges to edit this file.


networking will still start up during boot but it won't configure any interface.

If you actually want to prevent networking as a whole from running at boot then look at the command update-rc.d

---

### Post by Steff_DK on 2006-02-01
I put a # in front of the auto eth0 and eth1 but the boot process says:

```
...
Configuring network interfaces - ok
Waiting for network interface to come up
...
```

Where do I remove the waiting part? :confused:

---

