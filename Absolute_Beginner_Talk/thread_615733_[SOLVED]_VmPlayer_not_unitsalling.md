---
title: "[SOLVED] VmPlayer not unitsalling"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-11-17
Hi i have installed VMplayer using the add/remove and each time i get a software update it complains that it needs to prob for a subnet.
Anyway i want to uninstall it and try Virtual Box.
I tired removing it from add/remove and it said i needed to configure vmplayer using dpg --configure.

This is what happened:
```

Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.153.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.251.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1

Errors were encountered while processing:
 vmware-player

```

What should i do to uninstall this?

---

### Post by Arthur Archnix on 2007-11-17
It sounds like you can't remove it because it hasn't really finished installing. You should go ahead and do what it says about running dpkg -reconfigure and then once done, then try uninstalling.

---

### Post by pfwd.tech on 2007-11-18
Yep that worked. Thanks

---

