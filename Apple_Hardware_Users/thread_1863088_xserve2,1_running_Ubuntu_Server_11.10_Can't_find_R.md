---
title: "xserve2,1 running Ubuntu Server 11.10? Can't find RAID"
date: 2011-10-17
forum: Apple Hardware Users
---

### Post by rtackett on 2011-10-17
I have an old Apple XServe2,1 with Apple's SAS setup with a RAID0 array using two hard drives. I have OS X Server running on the XServe and have resized the OSX partition down to 100GB and created a second partition to house Ubuntu. 

I have the latest reFit running and showing the reFit boot menu successfully.

I have the Ubuntu Server 11.10 (64bit) booting via a USB drive successfully, and it detects my network cards and is able to set the time correctly via NTP during the Ubuntu Install. But, when it gets to the point of detecting the hard drives, the local SAS RAID cannot be found --- it just shows a prompt for iSCSI address setup, or "finish partition" --- when I choose "finish partition" it warns that no root partition could be found. 

I tried copying the 64 bit EFI files from the USB to the root HPF+ partition (/), copying the Install folder off of that same root and configuring a minimal grub.cfg similar to [http://ubuntuforums.org/showthread.php?t=1618922](http://ubuntuforums.org/showthread.php?t=1618922). Grub boots, but  it cannot find any folders off of (hd0) (unknown file system).

Has anyone had any luck getting Ubuntu installed on an Apple XServe2,1 with the hardware RAID setup? I've tried blowing the RAID away and not installing OSX/reFit, but Ubuntu install still cannot detect the drives.

---

