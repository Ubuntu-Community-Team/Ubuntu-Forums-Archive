---
title: "Vmware player issue"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by dlreynolds on 2007-02-21
Hello, I'm having a problem that I do not completely understand. I'm running Ubuntu 6.10 Edgy on a Gateway MX7525. I downloaded a program called Automatix and installed Vmware player. The program seems to run just fine, but is causing me some trouble. Whenever I try to install a new package, the package manager seems to want to reinstall Vmware.

I used apt-get install zsnes to install a snes emulator:

dlreynolds@dlreynolds-laptop:~$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zsnes is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.95.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] yes

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.225.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] no

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] no

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] n

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

I do not fully understand what is going on here.

If I try and remove vmware-player:

dlreynolds@dlreynolds-laptop:~$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 110873 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

I also tried to use dpkg-reconfigure:

dlreynolds@dlreynolds-laptop:~$ sudo dpkg-reconfigure vmware-player
/usr/sbin/dpkg-reconfigure: vmware-player is broken or not fully installed

I've tried to use the synaptic package manager and also the Add/Remove Ubuntu program, and I end up with the same problem. I would really like to get the vmware-player off my system and would appreciate any ideas that you all might have.

Thank you,
Daniel Reynolds

---

### Post by maniacmusician on 2007-02-21
Go into your Runlevel editor (probably called "Services") and halt any processes related to vmware-player. Then try to use aptitude to remove it: "sudo aptitude purge vmware-player"

If you're looking for good virtualization software, you might want to try [VirtualBox]("http://virtualbox.org")

---

### Post by dlreynolds on 2007-02-21
Worked like a charm, thank you very much.

---

### Post by nc_jed on 2007-05-27
I too had the exact same problem and was about to post a query regarding it.  Thanks to the 'Check if this is Already Posted' button I found the thread.  I too worked like a charm.  Props ManiacMusician.

---

