---
title: "ldconfig: File too large"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Matonen on 2007-03-24
Have no idea what i did but i cant install or uninstall anymore

This is what i get if i try to install:
> setting up: apt (0.6.45ubuntu14) ...
/var/lib/dpkg/info/apt.postinst: 41: ldconfig: File too large
dpkg: error processing apt (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)


tried:
```
sudo dpkg --configure -a

```

result:
> Setting up: apt (0.6.45ubuntu14) ...
/var/lib/dpkg/info/apt.postinst: 41: ldconfig: File too large
dpkg: error processing apt (--configure):
 subprocess post-installation script returned error exit status 2
Setting up: libnautilus-extension1 (2.16.1-0ubuntu3.2) ...
/var/lib/dpkg/info/libnautilus-extension1.postinst: 6: ldconfig: File too large
dpkg: error processing libnautilus-extension1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on libnautilus-extension1 (>= 2.15.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apt
 libnautilus-extension1
 nautilus


Tried also apt-get update, upgrade and dist-upgrade and no help

Thanks 

Matonen

---

### Post by Lord Illidan on 2007-03-24
Can you run ```
df -h
``` in terminal and post output here?

---

### Post by Matonen on 2007-03-24
> **Lord Illidan said:**
> Can you run ```
df -h
``` in terminal and post output here?

```

/dev/sdb1              19G  4,7G   14G  27% /
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  176K  9,9M   2% /proc/bus/usb
udev                   10M  176K  9,9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-11-generic/volatile
/dev/disk/by-uuid/383C740B3C73C284
                       56G   55G  879M  99% /media/disk1
/dev/disk/by-uuid/F02C43552C43164E
                       56G   55G  705M  99% /media/disk2
/dev/sda2              93G   61G   33G  66% /media/disk3
/dev/disk/by-uuid/280CE5900CE558F8
                       56G   51G  4,9G  92% /media/disk4
/dev/disk/by-uuid/76A0A35FA0A32499
                       93G  8,4G   85G   9% /media/disk5
/dev/disk/by-uuid/6A9088B2908885F3
                       93G   22G   72G  24% /media/disk6
/dev/disk/by-uuid/FCEC1E4CEC1E0216
                       20G  4,6G   16G  24% /media/disk7

```

---

### Post by Matonen on 2007-03-25
After night i trien again and everything is working again . have no idea what was the problem.

---

