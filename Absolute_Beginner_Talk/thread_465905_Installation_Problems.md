---
title: "Installation Problems"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by toose on 2007-06-06
Hey guys, 

I've got a bit of spare time today so I'd thought I'd finally get round to setting up a bit of a media/web server on a spare HDD in my PC. 

I started following [this guide](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1) and downloaded the live CD of Xubuntu 7.04. 

I booted into the LiveCD and tried installing the distro using the standard installer, however during installation I keep on getting this error: 

> 
The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

Does anybody know what this error is associated with partition wise and how to correct the problem?

I have tried disconnecting the all my other HDDs and using the GNOME partition editor but still no luck. 

My Specs:

AMD64 X2 4400+ (@ 2.6Ghz)
HIS X1900XT 512Mb
2GB Corsair XMS TwinX
SATA Maxtor 250GB DiamondMax 10 (only spare HDD)

Thanks,
toose

---

### Post by LaRoza on 2007-06-06
What was on this disk before, partitions, format, etc?
Did this hard disk work recently?

You could try wiping the entire disk, use GParted to delete all existing partitions, and then reformat it as a single primary partition with ext3 then try to install again.

---

### Post by toose on 2007-06-06
It was previously used as a storage drive for my Windows XP install. It works fine in Windows, I've booted back into windows and remove the partition from the drive via Disk Management and then tried the installation process and it still fails. 

I'll give formatting in Xubuntu a try and then try another install.

---

### Post by toose on 2007-06-06
Now, I've successfully been able to format my HDD to ext3 via GNOME Partition Editor on the Live CD but the installation problem still persists.

---

### Post by crazyclown on 2007-06-25
Did you get this working?  I am having the same issue.

---

