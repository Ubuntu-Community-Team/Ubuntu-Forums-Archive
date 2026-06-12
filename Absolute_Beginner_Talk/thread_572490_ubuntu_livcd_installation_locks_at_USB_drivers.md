---
title: "ubuntu livcd installation locks at USB drivers"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by dr.flodo on 2007-10-10
I am new to Ubuntu and need help installing it for the first time.

While trying to install Ubuntu 7.04 from the Live CD, the program locked up near the final step (for about 4 hours) with the bouncing processor indicator moving, and the screen message saying "Installing USB Devices...). 

After closing the locked Installation window and rebooting, there was no new boot menu, other than the pre-existing Windows boot manager, which still worked fine. I inspected the ext3 drive using Parted Magic LiveCD and found several GB of system files on an 18.2 GB ext3 partition, and an 820 MB Swap partition.

This installation was to occur onto a dedicated 20 GB drive on a system running Win XP on the other drives. During installation, the boot manager was specified to be on the C: drive. The destination was specified as "Guided using the entire disk".

Computer specs:
  Asus M2NBP-VM CSM motherboard
  AMD 64 4800+ CPU
  2GB RAM
  NVIDIA nForce Network Adapter (unplugged)
  Onboard Display adapter: NVIDIA Quadro NVS 2105/NVIDIA GeForce 6150LE
  HDD 0 Seagate IDE 160 GB backup drive FAT32
  HDD 1 Seagate IDE 20 GB ext3 (intended Ubuntu install drive)
  Extra SATA Drive with Win XP 250 GB multiple partitions, FAT32

Yearning for something to do with my new system I successfully used Parted Magic to resize the main partition smaller, delete the existing Swap and recreate a larger Swap partition.
 (partition 1 was created by Ubuntu install)
 (partition 2 is a Linux 2 GB Swap, increased from 833 MB to 2 GB)

Had I gone with manual installation, that would have been my choice for partitions. So now what. I don't know how to try booting into the installation drive, since it isn't drive 0 and I don't know how to build or edit the grub boot manager. Under Windows, there are no new files on the HDD0 C: drive that look like boot managers.

Any advice on where I went wrong or what to do to get Ubuntu installed correctly would be greatly appreciated.

---

### Post by Daveth on 2007-10-10
Hi.
Welcome to the ubuntu Forum. Sorry to hear about your installation woes. Might be worth reading this

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

as a guide to partitions. Did you burn the cd yourself, or is it a pre-made one? Did you also check the checksum, to look for disk errors?

This 

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

has a bit of info. Though there clearly are ubuntu system files on your hard drive, I would start again as it has not properly run through the install process. I'd run through this

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

in the first instance, then re-try- it ought to whizz through the install.

---

### Post by dr.flodo on 2007-10-27
Thanks Daveth, 
The ISO is fine. I can run ubuntu from the CD by hitting ctrl-alt-backspace from the locked up screen. The problem is that Ubuntu is not negotiating beyond some installation step around 91% that is required to install to the hard drive. I tried installing the Mepis Distro instead from a Live CD ISO and it installed fine. Also, I was able to install Ubuntu on a low end old computer.

This same problem of lockup during installation happens on my system even when using older versions of Ubuntu ISO CDs including the AMD64 bit version. There have been other users with similar problems in past posts. The common thread was that all of us had nVidia drivers, and I noticed that my nVidia drivers were not loaded on the CD. Alas, there seems to be some lack of awareness of this problem from the Ubuntu development team (your post excepted), and I suspect this may be turning new users away from using Ubuntu and from 'nix in general, since nVidia chips are quite common these days. My first post on this issue had more details, but was not replied to.

---

