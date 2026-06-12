---
title: "Restore grub with rEFInd on the mac mini with Mac OS X and Ubuntu OS."
date: 2013-11-02
forum: Apple Hardware Users
---

### Post by marietto2008 on 2013-11-02
Hello,

This is the partition table of my Mac Mini (old verson) :


Partition         File system       Mount Point     Label          Size                  Used              Unused            Flags

/dev/sda1       FAT32                                     EFI             200.00 MB        18.12 MB        181.88  MB        boot

/dev/sda2       hfs+                                        Mac HD        55.58 GB         28.02 GB         27.56  GB

/dev/sda5       ext4                                                            17.78 GB           7.41 GB         10.37  GB

/dev/sda6       linux-swap                                                 992.20  MB



I have installed rEFInd and on the boot screen I can choose between Mac OS and Ubuntu. Actually I can use only Mac OS because it is able to boot succesfully,but not Ubuntu because after a lot of messing grub is broken. I would like to know how can I boot Ubuntu again. I don't want to reinstall it from scratch,because the ubuntu partition is not damaged and my personal informations are good. Thanks.

---

### Post by pacome.heuze on 2013-11-04
Try to press alt button when you poweron your mac then if you did installed your ubuntu via boot camp you will have the choice on refit and windows (windows is actualy ubuntu strange to say it ;-).
if not i have no idea.

---

