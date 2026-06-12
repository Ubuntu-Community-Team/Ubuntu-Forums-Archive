---
title: "Re: Can't copy to firewire drive - no permission"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by jleaman on 2007-07-10
> **aysiu said:**
> Based on what I see, it looks as if it's /dev/sda2 that you're trying to mount with the correct permissions. Since it's a Linux partition, though, the problem probably lies in the *file* and *folder* permissions instead of the mounting parameters.

Try this: ```
sudo chown -R spazsui:spazsui /media/ieee1394disk
sudo chmod -R 755 /media/ieee1394disk
```

I am having this problem also, i have a FireWire 40gig drive i would like to use for backing up my pictures and email, as that is the most important stuff for me. When i go to copy stuff to the drive i get, You do not have permission to do this type of thing,.

Here is teh Sudo fdisk -l command to help :)

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4665    37471581   83  Linux
/dev/sda2            4666        4870     1646662+   5  Extended
/dev/sda5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38154    39069680    7  HPFS/NTFS
jase@jase-desktop:~$ 

thanks for the help in advance :)

---

### Post by aysiu on 2007-07-10
Actually, your problem is quite different, so I've made it into its own thread.

Your Firewire drive looks NTFS, which is read-only by default.

To make it read/write follow this tutorial:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by jleaman on 2007-07-10
You, know this is exactly why i moved to Ubuntu, it's people like you that help us newbies and it sooooooo nice, i wish there wa ssoemthing i could do to contribute :) Did i mention im Dell DCSE certified and other things :) Ton's of hardware certifications like printers laptops etc etc I hope to help out here more, soon.

Jase..

P.s good work thanks so much.

There is no NTFS config in my menue, and i dont see any where in the Add/Remove applications tool to install it. ?

---

### Post by jleaman on 2007-07-10
sudo apt-get install ntfs-config ok i ran this, then looked in the menue still nothing, what should i do ?

---

### Post by Papi-KB7VGW on 2007-07-10
Synaptic has the driver.  It is called ntfs-3g  Make sure all of software repositories are checked in software sources.  It works quite well:)

---

### Post by regomodo on 2007-07-10
ermm. isn't /dev/sda2 the extended bit of the swap partition?

---

