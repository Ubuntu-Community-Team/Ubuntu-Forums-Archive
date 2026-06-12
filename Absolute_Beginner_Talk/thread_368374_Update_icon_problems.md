---
title: "Update icon problems"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-02-23
I have the update icon showing, but when I click on it, I'm told that I must close adept or Synaptic, but neither of them are open. This occurs right after I reboot too. I can use synaptic and adept anyway, and they are capable of add/removing programs.

---

### Post by bapoumba on 2007-02-23
Hello,
please make sure they are not in the startup program (> System > Preferences > Sessions. update-notifier should be, but not adept/synaptic), open a terminal (> Accessories > Terminal) and run:
```
sudo aptitude clean
sudo aptitude update
```
and report here any error.

---

### Post by macruadhi on 2007-02-23
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
Building tag database... Done
W: Could not lock the cache file.  Opening in read-only mode; any changes you make to the states of packages will NOT be preserved!
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
eric@eric-laptop:~$

---

### Post by bapoumba on 2007-02-23
Then run:
```
sudo dpkg --configure -a
```
and report the errors.

edit: what is the output to **ls -la /var/lib/dpkg/lock** ?
did you exit synaptic or adept abnormally ?

---

### Post by macruadhi on 2007-02-23
eric@eric-laptop:~$ sudo dpkg --configure -a
Password:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.211.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] y

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.125.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

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
eric@eric-laptop:~$

---

### Post by macruadhi on 2007-02-23
eric@eric-laptop:~$ sudo dpkg --configure -a
Password:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.211.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] y

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.125.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

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
eric@eric-laptop:~$   






AND
eric@eric-laptop:~$  ls -la /var/lib/dpkg/lock
-rw-r----- 1 root root 0 2007-02-23 10:28 /var/lib/dpkg/lock

---

### Post by bapoumba on 2007-02-23
If this is an issue with vmware, have a look [here]("http://www.ubuntuforums.org/showthread.php?t=315493"). Last pages have recent posts.

edit : the lock should be okay now. If not, rename it in lock.old, and a new one will be created if needed.

---

