---
title: "Automatix stuck on installing VMware-player"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Talako on 2007-03-17
Yo,
I installed automatix a while ago, and installed a whole bunch of packages with it, the only one I had a problem with was VMWare-Player, I guess it installed OK, but now whenever I install something, it probes for a subnet or something to that effect, and I have tried unselecting it in synaptic, but it fails while uninstalling it. This situation wouldn't be a problem except that now I am looking to install VMWare Server to play around and run Windows inside, but it won't install with a previous version of VMWare software. I am kindof on the new side to messing with this stuff, I have left it alone for a while, but, like I said, now it's an issue. Has anyone had the same problem? Anyone have ideas for a solution?
Thanks!

---

### Post by jackrobinson on 2007-03-17
> **Talako said:**
> Yo,
I installed automatix a while ago, and installed a whole bunch of packages with it, the only one I had a problem with was VMWare-Player, I guess it installed OK, but now whenever I install something, it probes for a subnet or something to that effect, and I have tried unselecting it in synaptic, but it fails while uninstalling it. This situation wouldn't be a problem except that now I am looking to install VMWare Server to play around and run Windows inside, but it won't install with a previous version of VMWare software. I am kindof on the new side to messing with this stuff, I have left it alone for a while, but, like I said, now it's an issue. Has anyone had the same problem? Anyone have ideas for a solution?
Thanks!

uninstall vmware-player from automatix (not synaptic)

---

### Post by Talako on 2007-03-17
Only problem is that Automatix thinks that VMPlayer is not installed.
Any other Ideas?

---

### Post by jackrobinson on 2007-03-17
> **Talako said:**
> Only problem is that Automatix thinks that VMPlayer is not installed.
Any other Ideas?

ok what does the following give?
```
sudo apt-get remove vmware-player
```

---

### Post by Talako on 2007-03-19
```
mariot@falcon1-ubuntu:~$ sudo apt-get remove vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 181100 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
***
* Updating MIME database in /usr/share/mime...
Wrote 483 strings at 20 - 282c
Wrote aliases at 282c - 29e0
Wrote parents at 29e0 - 33c0
Wrote literal globs at 33c0 - 3424
Wrote suffix globs at 3424 - 681c
Wrote full globs at 681c - 6840
Wrote magic at 6840 - bee0
Wrote namespace list at bee0 - bef0
***
mariot@falcon1-ubuntu:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

mariot@falcon1-ubuntu:~/vmware-server-distrib$ sudo apt-get autoremove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vmware-player is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mariot@falcon1-ubuntu:~/vmware-server-distrib$ 

```

---

### Post by in_flu_ence on 2007-03-19
So i suppose you have vmware-player under the 'install' tab in automatix. Install it once again and uninstall it. Hopefully this will remove the package completely.

If you want to use vmware-server, download the binary from vmware site and follow their installation guide. It is fairly straight forward with very little trial and error. Or you can try virtual box straight from automatix.

Good Luck

---

### Post by jackrobinson on 2007-03-19
> **Talako said:**
> ```
mariot@falcon1-ubuntu:~$ sudo apt-get remove vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 181100 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
***
* Updating MIME database in /usr/share/mime...
Wrote 483 strings at 20 - 282c
Wrote aliases at 282c - 29e0
Wrote parents at 29e0 - 33c0
Wrote literal globs at 33c0 - 3424
Wrote suffix globs at 3424 - 681c
Wrote full globs at 681c - 6840
Wrote magic at 6840 - bee0
Wrote namespace list at bee0 - bef0
***
mariot@falcon1-ubuntu:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

mariot@falcon1-ubuntu:~/vmware-server-distrib$ sudo apt-get autoremove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vmware-player is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mariot@falcon1-ubuntu:~/vmware-server-distrib$ 

```
well the vmware-player package is gone but it has left some its cruft behind..
try doing the following:
```
sudo rm -f /etc/init.d/vmware-player
sudo rm -f /etc/rc0.d/K20vmware-player
sudo rm -f /etc/rc1.d/K20vmware-player
sudo rm -f /etc/rc2.d/K20vmware-player
sudo rm -f /etc/rc3.d/K20vmware-player
sudo rm -f /etc/rc4.d/K20vmware-player
sudo rm -f /etc/rc5.d/K20vmware-player
sudo rm -f /etc/rc6.d/K20vmware-player
```
and then run the vmware-server installer

---

