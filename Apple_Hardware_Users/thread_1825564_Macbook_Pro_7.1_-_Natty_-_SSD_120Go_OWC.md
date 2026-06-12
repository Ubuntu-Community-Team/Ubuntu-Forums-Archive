---
title: "Macbook Pro 7.1 - Natty - SSD 120Go OWC"
date: 2011-08-15
forum: Apple Hardware Users
---

### Post by skuld78 on 2011-08-15
Hi,


I tri to install Ubuntu on my Macbook Pro with an SSD drive, but it fails.

1 ) If I format my partition with ext4 or btrfs, the installation seems to freeze. So i choose ext3 now.

2 ) MacOS boot in a few second, but ubuntu have a lot of bug at startup. Timeout on the SSD discovering, the interface is recognize as IDE, but should be SATA. 
So it take ~5minutes to boot !!

3) a hdparm -t return 110Mb/s :'( :'( :'(


Please help :'( :'(

---

### Post by metatechbe on 2011-08-15
> **skuld78 said:**
> the interface is recognize as IDE, but should be SATA. 


In BIOS mode, the interface is by default in legacy IDE mode.
In EFI mode, the interface is by default in SATA AHCI mode.
But the following is a workaround : 
[http://ubuntuforums.org/showpost.php?p=10685211&postcount=230](http://ubuntuforums.org/showpost.php?p=10685211&postcount=230)

---

