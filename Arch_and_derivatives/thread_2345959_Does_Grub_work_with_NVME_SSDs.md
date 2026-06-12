---
title: "Does Grub work with NVME SSDs?"
date: 2016-12-09
forum: Arch and derivatives
---

### Post by CarpCharacin on 2016-12-09
I read a while back that some people ere having issues with grub when using NVME ssds.  Is it fixed now or not?

---

### Post by oldfred on 2016-12-09
In some cases it is not grub, but vendors UEFI/BIOS

 Asus NVMe issues - not solved UEFI/BIOS issue?
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
[http://ubuntuforums.org/showthread.php?t=2325056](http://ubuntuforums.org/showthread.php?t=2325056)
Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162)
spec entry for nvme devices (UEFI v2.4A 9.3.5.22)

---

### Post by CarpCharacin on 2016-12-10
The board works with SSDs.  I just don't want to install a bootloader that dosen't work.  I read a post from a few months ago on the arch forums that grub didn't work with nvme drives.

---

### Post by oldfred on 2016-12-10
Several users discuss NMVe installs, often vendor issues or configuration settings in UEFI.
[https://ubuntuforums.org/archive/index.php/t-2325056.html](https://ubuntuforums.org/archive/index.php/t-2325056.html)
[https://ubuntuforums.org/archive/index.php/t-2286856.html](https://ubuntuforums.org/archive/index.php/t-2286856.html)

[https://ubuntuforums.org/showthread.php?t=2325056&p=13506018#post13506018](https://ubuntuforums.org/showthread.php?t=2325056&p=13506018#post13506018)
The NVME drive is recognized in Ubuntu using a different convention. Instead of */dev/sda*, */dev/sdb*, etc. you get */dev/nvme0n1, /dev/nvme0n2* etc. Note the first drive is *n1*. The partitions within the drives are *p1, p2*, etc. 

The only way to know for sure if it works with your system is to try it. All it takes is a little time.

---

### Post by CarpCharacin on 2016-12-11
Is there anyone that has used it?

---

