---
title: "vmware  - player install problems."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by bamend on 2007-07-06
I tried to install Automatix2 and the vmware setup is going in circles.  I keep on getting this below and I can not add any more programs.  
I have tried to remove vmware in the Synaptic deal but I can not get rid of it.  Please help.



sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.20-16
The following NEW packages will be installed:
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.20-16
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/1691kB of archives.
After unpacking 4407kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package vmware-player-kernel-modules-2.6.20-16.
(Reading database ... 136827 files and directories currently installed.)
Unpacking vmware-player-kernel-modules-2.6.20-16 (from .../vmware-player-kernel-modules-2.6.20-16_2.6.20.5-16.29_i386.deb) ...
Selecting previously deselected package vmware-player-kernel-modules.
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.20.16.28.1_i386.deb) ...
Setting up vmware-player-kernel-modules-2.6.20-16 (2.6.20.5-16.29) ...

Setting up vmware-player-kernel-modules (2.6.20.16.28.1) ...
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.33.0/255.255.255.0 appears to be unused.

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

The subnet 172.16.196.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
bamend@amend:~$

---

### Post by ghostshadow189 on 2007-07-07
oh , i also have this problem , some1 help us pls?

---

### Post by mikeyphi on 2007-07-07
If you're having problems after removing VMWare - you need to take a deep breath, find every file with VMWare in the title and manually delete!!! Then you will be able to start again but perhaps not using Automatix

---

### Post by seshomaru samma on 2007-07-07
try 
```
apt-get remove --purge vmware
```
or maybe ```

apt-get remove --purge vmware-server
```

---

