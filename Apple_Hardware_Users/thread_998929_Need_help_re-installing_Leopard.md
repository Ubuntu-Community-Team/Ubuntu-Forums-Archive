---
title: "Need help re-installing Leopard"
date: 2008-12-01
forum: Apple Hardware Users
---

### Post by rcame on 2008-12-01
Hey everyone,

I'm brand new to Linux so I accidentally completely removed the Apple OS and installed Ubuntu. I would prefer to have my HDD split in half (allowing for half OS X and half Ubuntu), but when I boot from the Leopard install DVD I can't see my now Ubuntu Hard drive as one of the choices to install Leopard on.

I'm on the first generation MacBook Pro, and I just need to know how to completely wipe Ubuntu from my HDD so I can re-install Leopard.

Thanks.

---

### Post by DGortze380 on 2008-12-01
back up any important data
boot your ubuntu live cd
run the program gparted (open terminal, type sudo gparted)
delete all partitions
shutdown
reboot with your leopard dvd in the drive
hold 'c' to boot from the dvd drive
use the disk utility on your dvd to create a new HFS+ partition for OS X
install to the HFS+ partition


I would suggest not partitioning half and half. Leave like 3/4 of your drive for OS X. 

Ubuntu really only needs 20 GBs at most, especially because you can mount your OS X partition in Ubuntu and access your files from there.

---

### Post by cyberdork33 on 2008-12-01
You need to repartition the disk with DiskUtility after booting the Leopard disc in order to be able to install again. After you do that, use Bootcamp to create your Ubuntu partition. See this post:
[http://ubuntuforums.org/showpost.php?p=6211925&postcount=2](http://ubuntuforums.org/showpost.php?p=6211925&postcount=2)

---

