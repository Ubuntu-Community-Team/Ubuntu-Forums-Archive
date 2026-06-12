---
title: "Another Dual-Boot question!"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ZYxman on 2007-04-11
Hi,

First, sry for my nickname (I was in a hurry and missed the time to release Shift =P).

I have already installed Ubuntu 5.10 and it dual-booted ok (I followed a tutorial).

Now, I reinstalled Windows some time ago and it messed up with linux, it won't boot. And now I need to install linux again and decided to install 6.10. Can I just keep my partitions? (See attach).

Can I just use the desktop CD (and hope it will detect Windows, and problably will install grub in the first hd MBR) or I have to burn the "alternate CD" and follow the not-so-easy way to dual boot?

Thanks,

Zyxman.

---

### Post by confused57 on 2007-04-11
> **ZYxman said:**
> Hi,

First, sry for my nickname (I was in a hurry and missed the time to release Shift =P).

I have already installed Ubuntu 5.10 and it dual-booted ok (I followed a tutorial).

Now, I reinstalled Windows some time ago and it messed up with linux, it won't boot. And now I need to install linux again and decided to install 6.10. Can I just keep my partitions? (See attach).

Can I just use the desktop CD (and hope it will detect Windows, and problably will install grub in the first hd MBR) or I have to burn the "alternate CD" and follow the not-so-easy way to dual boot?

Thanks,

Zyxman.
You shouldn't have any problems with the live cd, just choose your current partitions for Ubuntu, select the larger as (/) mountpoint, and the smaller as swap...choose to format your (/) as ext3 and swap as swap.  Grub will install to your Window's drive mbr, if it is set to boot first in bios(before your Ubuntu drive), an entry should be added to grub to boot Windows.  Just make sure not to check format for your Windows & FAT partitions.
The 2nd link in my signature has some excellent screenshots for installing with the desktop cd.

Alternatively, you could set the drive  you're going to install Ubuntu on in bios to boot before your Window's drive, before you boot up the live cd to install Ubuntu.  The installer should install grub to the mbr of the Ubuntu drive & add an entry to boot Windows.  This way if you're not able to boot Ubuntu, then you could change the boot order to boot Windows.
See the 3rd link in my signature for how I have my system set up.

Added:  Barfbag's suggestion would be the easiest, you'd need to select Manual partitioning to install the way I mentioned.

---

### Post by BarfBag on 2007-04-11
I find it easier to delete your Linux partitions, and tell the Ubuntu installer to install to the "largest contiguous free space."  You can delete them by going into disk management (the screen shot), right clicking on each of the partitions, and hitting delete.

---

### Post by ZYxman on 2007-04-11
@confused57

Thanks man! I'will try the first option, Windows is easy to fix anyway (and I really have to reinstall it).

@up

OK, but choosing by hand I think it's easier to not to mess up with my "SHARED" FAT32 partition, I'will just format the 15 gb ext3(sdb2 I think, not sure...) and mout to "/" and format swap again... Is that correct?

Thanks

---

### Post by confused57 on 2007-04-11
> **ZYxman said:**
> @confused57

Thanks man! I'will try the first option, Windows is easy to fix anyway (and I really have to reinstall it).

@up

OK, but choosing by hand I think it's easier to not to mess up with my "SHARED" FAT32 partition, I'will just format the 15 gb ext3(sdb2 I think, not sure...) and mout to "/" and format swap again... Is that correct?

Thanks

That sounds right, you could also do what Barfbag suggested by deleting both partitions & doing it the way he mentioned...or just select manual partitioning & do the way you've described, don't format the FAT32 & the installer should take care of the rest.

---

