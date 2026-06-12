---
title: "I broke apt-get, Help!"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2007-02-20
I tried installing vmware through aptitude, and somehow it didn't finish installing.  Now I can't finish installing it, and I can't remove it.  Now I can't upgrade or install anything else until I resolve the issue.  Here is a little output:
> sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have unmet dependencies:
  vmware-player: Depends: vmware-player-kernel-modules but it is not installable
                 Depends: libssl0.9.7 but it is not installable


I've tried to remove everything independently and together, but nothing seems to work. 
Here is the output when I try to remove vmware-player:
> sudo aptitude remove vmware-player
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  vmware-player
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.1MB will be freed.
Writing extended state information... Done
(Reading database ... 117955 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
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
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
ceedub@ceedub-laptop:~$                                      

What do I do now?

---

### Post by Bachstelze on 2007-02-20
Try :

```
sudo apt-get -f install
```

---

### Post by CeeDub on 2007-02-20
I tried that too, but I get the same result as upgrade.

---

### Post by Bachstelze on 2007-02-20
And how about this ?

```
sudo apt-get -f remove
```

---

### Post by CeeDub on 2007-02-20
still nothing.  I get the same thing.  vmware player tries to configure itseld, fails and exits.

---

### Post by Bachstelze on 2007-02-20
Funy, since it's a broken package, apt-get -f should remove it... Well, I guess you can always removing it with *dpkg -r*.

---

### Post by CeeDub on 2007-02-20
Well, I don't know how I did it, but I did it.  I finally got rid of it.  Thanks for your help, HymnToLife.

---

