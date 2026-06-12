---
title: "Cant remove vmplayer"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by s_raghu20 on 2007-07-20
Hi,

I have installed vmware player from someone's advice. However since it does not allow creation of a new virtual machine, I plan to remove this and install vmware server instead.

But, I dont seem to be able to find a way to remove vmware-player.

Here's the current output...

> 
raghav@hpubuntu:~$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 59747 files and directories currently installed.)
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
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
raghav@hpubuntu:~$ 



I tried various options with apt get, force, -t as well.. but nothing helps...

Any idea.. anybody...

all help is appreciated.

regards
raghav..

---

### Post by FunkyJack on 2007-07-20
Try:

```
sudo dpkg -P vmware-playe
```

---

