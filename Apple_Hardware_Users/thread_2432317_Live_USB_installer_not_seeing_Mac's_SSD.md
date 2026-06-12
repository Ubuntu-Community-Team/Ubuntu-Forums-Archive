---
title: "Live USB installer not seeing Mac's SSD"
date: 2019-11-30
forum: Apple Hardware Users
---

### Post by Garrett_44 on 2019-11-30
I'm attempting to install Ubuntu 19.10 on a Mac laptop with an SSD  hard drive (specs below) that's been partitioned with a FAT32 GUID  partition. I have a working USB installer, rEFIt is installed and can  boot from the USB pen drive without a problem. When I launch the Ubuntu  installer to install from the USB live session to Mac's SSD, it does not  'see' any hard drives other than the USB pen drive, jumps the installer  step to select where to install and states:


  "You need at least 8.6 GB disk space to install Ubuntu. The computer has only 7.7 GB." - It's an 8 GB USB pen drive, so no doubt this is the pen drive.
  
SIP is disabled on the mac and I've also disabled all startup disk  restrictions. I see comments online about needing to wait for Ubuntu  19.10 because NVMe storage isn't supported until Kernal 5.1.5 ([Ubuntu installer can't see Mac HDD]("https://askubuntu.com/questions/1005504/ubuntu-installer-cant-see-mac-hdd"))  - check using that. Also, seeing comments about changing SATA from IDE  to ACHI, some say this is unnecessary on a mac, but I tried doing this  (based on instructions here: [How to switch from IDE to AHCI]("https://askubuntu.com/questions/976071/how-to-switch-from-ide-to-ahci")) and I can't because the pen drive is read-only - update-initramfs -u will fail.

  
Does anyone know how to resolve this? Why the installer can't see the Mac's SSD?

-----------
Macbook Pro (15 inch, 2019) 2.6 GHz Intel Core i7, OSX 10.14.6 (Mojave)

---

### Post by uRock on 2019-11-30
Moved to ***"Apple Hardware Users"*** for better visibility.

---

### Post by ozfrog on 2019-12-08
[https://florisvanbreugel.wordpress.com/2018/03/23/installing-ubuntu-on-an-external-ssd-drive-on-a-macbook/](https://florisvanbreugel.wordpress.com/2018/03/23/installing-ubuntu-on-an-external-ssd-drive-on-a-macbook/)

This worked for me - MBPro OS 10.14.6 Installation to 32G USB thumb drive.
Took some time nutting it out - but finally "persistent" installation - all tweaks and software are saved./

---

