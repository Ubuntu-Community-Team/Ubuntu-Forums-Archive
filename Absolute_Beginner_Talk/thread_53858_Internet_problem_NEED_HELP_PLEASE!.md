---
title: "Internet problem NEED HELP PLEASE!"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by tobiwan on 2005-08-02
Hello all,

Ok here is the prob. I installed ubuntu yesterday.. but i just cant get my internet working. I have a cable broadband conection. and my network hardware seems to work properly. Can someone help me with this prob?

---

### Post by ubuntu_demon on 2005-08-02
please post the results (without the $) of the following commands (in your terminal) :

$ ifconfig
$ cat /etc/network/interfaces
$ lspci

If your /etc/network/interfaces doesn't look like this :

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

```

then please post your old /etc/network/interfaces and try to replace it with this one

Als try this command :

$sudo ifdown eth0 ; sudo ifup eth0

---

### Post by tobiwan on 2005-08-02
ok the problem has been fixed! thnx Demon!

---

### Post by ubuntu_demon on 2005-08-02
[QUOTE=tobiwan]ok the problem has been fixed! thnx Demon![/QUOTE]
 what did you do exactly to fix it ?

---

