---
title: "How do I see all my other files"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by naturalhl2 on 2005-12-18
How can I find my other media on my hdd using the live cd?

---

### Post by aysiu on 2005-12-18
You have to mount the hard drive.
Are the files you're looking for on a Mac or Windows PC?
Can you open up a terminal and post here the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

The terminal is in Applications > Accessories > Terminal

---

### Post by naturalhl2 on 2005-12-18
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    7  HPFS/NTFS
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/casper-snapshot
                      2.0G  1.5G  384M  80% /
tmpfs                 506M  4.0K  506M   1% /dev/shm
tmpfs                 506M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
tmpfs                 506M  980K  505M   1% /tmp
tmpfs                  10M  2.9M  7.2M  29% /dev

thats what I get how can I acess these files??

---

