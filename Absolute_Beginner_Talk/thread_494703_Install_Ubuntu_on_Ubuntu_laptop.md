---
title: "Install Ubuntu on Ubuntu laptop"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by felin on 2007-07-07
Hi - I decided to get rid of an old install of Ubuntu and install a fresh 7.04. Everything seems ok, but when the scanner checks drives before boot (every 30 boots) I get error messages. I was just checking whether all this seems right as regards partitions?

> **sudo fdisk -l**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

**df -Th**
Filesystem Type    Size Used Avail Use% Mounted on
/dev/sda1     ext3     71G  3.0G   64G   5% /
varrun       tmpfs   1014M  112K 1013M   1% /var/run
varlock      tmpfs   1014M     0 1014M   0% /var/lock
procbususb   usbfs   1014M  104K 1013M   1% /proc/bus/usb
udev         tmpfs   1014M  104K 1013M   1% /dev
devshm       tmpfs   1014M     0 1014M   0% /dev/shm
lrm          tmpfs   1014M   33M  981M   4% /lib/modules/2.6.20-16-generic/volatile

Would be grateful if someone could let me know if they think my partitions etc look ok?

---

### Post by aquavitae on 2007-07-07
Did you only get the errors once, or is it every time?  What are the errors?  I got some timestamp errors straight after insalling 7.04, by this was due to, my clock being incorrect, and corrected by ubuntu.  Nothing serious!

---

