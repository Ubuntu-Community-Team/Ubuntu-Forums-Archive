---
title: "RAID1 and Grub"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2008-03-15
I followed these instructions [here]("http://advosys.ca/viewpoints/2007/0/setting-up-software-raid-in-ubuntu-server/"), until I got to the section on Making every drive bootable. Where it says...

>     * Mount the md0 RAID device and use chroot and grub to install the bootloader onto both sda and sdb using the following commands

    mount /dev/md0 /mnt
    chroot /mnt
    grub
    device (hd0) /dev/sda
    root (hd0,0)
    setup (hd0)
    device (hd1) /dev/sdb
    root (hd1,0)
    setup (hd1)
    quit

mount /dev/mdo /mnt throws me an invalid argument failure. 

Advice?

---

### Post by dstew on 2008-03-15
> mount /dev/mdo /mnt throws me an invalid argument failure. I am sure it is a typo. The device name should be /dev/md0, not /dev/mdo.

Did you create the RAID device successfully?```
sudo mdadm --query /dev/md0
```When you try to mount it, what is the exact error message? You probably have to use sudo to mount the array. Also, you need to have a mount point:```
sudo mkdir /mnt/md0
sudo mount /dev/md0 /mnt/md0
```

---

### Post by ant2ne on 2008-03-15
**AH HA !!!**

```
ant2ne@2ne-buntu:~$ sudo mdadm --query /dev/md0
[sudo] password for ant2ne:
/dev/md0: 7.45GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.
ant2ne@2ne-buntu:~$ sudo mount /dev/md0 /mnt/md0
/dev/md0 looks like swapspace - not mounted
mount: you must specify the filesystem type
ant2ne@2ne-buntu:~$ 
```

the tutorial assumes that 0 was the root file. I put swap there because I heard that swap is faster at the center of the disk. Probably a moot point with 8 gigs of ram, but why not give it a try.

I will now continue with the tutorial and report any further problems. Thanks!!

---

