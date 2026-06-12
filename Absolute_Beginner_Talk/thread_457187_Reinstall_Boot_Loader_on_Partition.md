---
title: "Reinstall Boot Loader on Partition"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by mikaelsnavy on 2007-05-28
Hello,
I have Ubuntu (feisty) installed on /dev/sda6. I need to reinstall the boot loader on this partition (not the MBR). It has to do with the grub-install command on the install disk but I cannot get it to work. Anyone know how I can get this to work?
Thanks,
Mikael

---

### Post by b_martinez on 2007-05-28
sudo grub --install /dev/sda6 should work. 
I haven't booted with the install disk, but does it have an option to re-install the bootloader?
You may need to do more than just install to the  root partition.  If this is the case, you'll need to  also do 
grub find stage 1.5 
OR
grub --setup /dev/sda6
I think [or maybe I'm totally off base with this]
hth
Bill

---

### Post by mikaelsnavy on 2007-05-28
This gets me to a prompt "grub>" where I assume that I enter the configuration for the boot loader. Does anyone by change have a sample of this?
Thanks A Lot,
Mikael

---

