---
title: "2 problem: eth0 and graphics on boot"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by mschievano on 2006-02-02
like the topic say:
1. when I boot on dapper, the graphics with ubuntu on top and the services that starts on bottom is very horrible! The LCD monitor says that "there's a problem of resolution - Auto mode is trying to adj the page" I think that is because the screen is about a 400x300 (strange size...).

Q: What kind of file may I have to change to resume a beautiful 1024x768 boot?

2. When the gdm start, the resolution turn correctly to 1024x768. but even if the eth0 is (seems) ok and started with dhcp (I have a router modem ADSL) when I try to browse the web, nothing happen and errors occour. I if disable and reenable the eth0, all goes ok. This is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0
iface eth0 inet dhcp
provider dsl-provider

```

;)

---

### Post by mschievano on 2006-02-02
for network now is ok: i've add an a before the inet script.

Remain the problem on graph boot.

Thanks for who will help me.

---

### Post by mschievano on 2006-02-03
nothing

---

### Post by ace2005 on 2006-02-03
Step 3 from this How To will do it:

[http://ubuntuforums.org/showthread.php?t=41709](http://ubuntuforums.org/showthread.php?t=41709)

---

### Post by mschievano on 2006-02-04
[QUOTE=ace2005]Step 3 from this How To will do it:

[http://ubuntuforums.org/showthread.php?t=41709](http://ubuntuforums.org/showthread.php?t=41709)[/QUOTE]

Sorry, i didn't report that I've already try to put a 791 or 792 after a vga= in menu.lst

In this case, I see a black screen till the GDM appear :-k

---

### Post by mschievano on 2006-02-05
i use usplash now , and i see a little ubuntu logo in a big and dark screen.
Better than before...

---

