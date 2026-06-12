---
title: "Boot from USB devices.."
date: 2005-06-14
forum: Apple PPC Users
---

### Post by blacking on 2005-06-14
Hello list,

i would like to boot a minimal configuration of Linux ppc (vmlinux - initrd ecc) from my devices usb. At the moment, after the setup of the disk with mac-fdisk (dev/sda2 - boot and /dev/sda3 the root) and after mkofboot ecc ecc i can seen my usb devices when reboot my pb. But then select it, the usb disk image, the system show the standard choiche of linux l - x - c and do not my label for teh usb drive. If i select the letter l, the system recall another time the standard windows l - x - c; now if i repeate the choice -l-, Ubuntu Hoary start well. I do not received nothing hard error or kernel panic, but only a double master windows..


I think the problem is yaboot.conf not correctly configured inside my disk  /dev/sda2. 

Please does anyone here can support me, how to write a correct yaboot.conf, for start from an usb devices

TIA
Marco

---

