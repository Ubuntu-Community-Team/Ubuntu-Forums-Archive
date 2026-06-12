---
title: "VMware Server - resize partition"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-07-12
Seems many of us are having difficulty resizing a virtual partition in VMware Server.

Has anyone been successful doing this?
Anyone got a definitive answer from [www.vmware.com](www.vmware.com) regarding this?

Carl

---

### Post by 56seeker on 2007-07-12
I'm not sure if you're refering to a partition on your VMware server or a partition on a virtual machine; can you be a bit more specific?

---

### Post by titanevn on 2007-07-12
> **cwmoser said:**
> Seems many of us are having difficulty resizing a virtual partition in VMware Server.

Has anyone been successful doing this?
Anyone got a definitive answer from [www.vmware.com](www.vmware.com) regarding this?

Carl

This is a tutorial to resize Virtual HDD of Virtual Machine. I found a post on the Internet. try this!

1) On the Host Machine: stop the Virtual machine that you need to allocate more HDD space to.
2) Run C:\Program Files\VMware\VMware Server\vmware-vdiskmanager.exe to re-size the vmdk file. This will resize the HDD but not the partition.
For example: C:\Program Files\VMware\VMware Server>vmware-vdiskmanager.exe -x 80Gb -t 1 &#8220;C:\Virtual Machines\Viper\Windows Server 2003 Enterprise Edition.vmdk&#8221;
3) Exit BootIt and restart the virtual machine.
4) On the virtual machine: Download a copy of BootIt NG (Boot It Next Generation). [http://www.terabyteunlimited.com/downloads/bootitng.zip](http://www.terabyteunlimited.com/downloads/bootitng.zip)
5) Run the .exe and create a bootable CD ISO. Make sure you include the VGA drivers in the options!.
6) Copy the ISO to a different machine (eg the Host server) or a network location. For example: C:\BOOTITNG.ISO
7) On the Host machine: set the virtual machine to use the BootIt ISO as the CD Drive.
8) Start the Virtual Machine: hit ESC to bring up the boot manager as VMWare is loading and select to boot off the CD Drive with the ISO loaded.
9) When the BootIt GUI starts, resize the partition.
10) Restart the Virtual machine.

---

### Post by cwmoser on 2007-07-12
titanenv, you provided the solution!!!  I followed your suggestion and was able to resize both my WIndows virtual partitions in VMware Server from 8GB to 16GB.

Some notes I would like to add:
  - I had tried a similar process but used GPARTED to resize the partition rather than your suggestion to use BOOTITNG.  GPARTED will not resize a vmware partition properly.  BOOTITNG works.

  - I created a boot CDROM with the BOOTITNG.ISO image.  Select Cancel when it asks to install on the Hard Drive -- this will put you in Maintenance mode.  Then Resize.

  - If you get an error from Resize, boot your virtual machine and schedule a CHKDSK on next reboot to get a clean volume.

So, thanks for the solution to resizing a VMware virtual partition.

Carl

---

