---
title: "Is Triple OS Boot"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Khalis7 on 2008-02-22
Hi.. I'm just curious about triple OS boot problem. Right now, my 80Gb HDD contains WinXP and Ubuntu 7.10 and  configured by dual boot. Now, I would like to add new flavor of distro which is Fedora 8  to the current HDD and make it triple boot in overall.

 But, I wonder is there any problem going to be encountered in terms of compatibility? Will my current grub setting will be reset? FYI, I have another empty separate partition that's intended to be used for Fedora 8 installation. 

Any help and opinions are greatly welcomed.

---

### Post by Duck2006 on 2008-02-22
> **Khalis7 said:**
> Hi.. I'm just curious about triple OS boot problem. Right now, my 80Gb HDD contains WinXP and Ubuntu 7.10 and  configured by dual boot. Now, I would like to add new flavor of distro which is Fedora 8  to the current HDD and make it triple boot in overall.

 But, I wonder is there any problem going to be encountered in terms of compatibility? Will my current grub setting will be reset? FYI, I have another empty separate partition that's intended to be used for Fedora 8 installation. 

Any help and opinions are greatly welcomed.

Fedora will place it's own grub into the MBR and should pickup the ubuntu install, if it don't just edit the fedora grub.conf file and add the new lines to be able to run ubuntu.

---

### Post by sandysandy on 2008-02-22
> **Khalis7 said:**
> Hi.. I'm just curious about triple OS boot problem. Right now, my 80Gb HDD contains WinXP and Ubuntu 7.10 and  configured by dual boot. Now, I would like to add new flavor of distro which is Fedora 8  to the current HDD and make it triple boot in overall.

 But, I wonder is there any problem going to be encountered in terms of compatibility? Will my current grub setting will be reset? FYI, I have another empty separate partition that's intended to be used for Fedora 8 installation. 

Any help and opinions are greatly welcomed.

i am booting several linux distros and Win XP with no problems. if u run into problem u can edit menu.lst file of ubuntu so that correct partition info is shown against each distro. then u can use Super Grub Disk to load ubuntu&#347; GRUB back on MBR (I am assuming u will be more comfortable working on menu.lst file of ubuntu than Fedora)

regards

---

