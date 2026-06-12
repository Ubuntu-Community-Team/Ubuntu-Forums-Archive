---
title: "Grub problem..."
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by elmagozizou on 2005-07-13
Hi..I just install ubuntu, but know i have a litle problem,...there is the thing...

Before I install, I was runnning windows XP in and suse...they were booting from grub fine (Grub was placed in MBR), then i install ubuntu, so I delete (from the ubuntu installation) the suse partitions and install the ubunutu system in the free space that left. The ubunutu installation recognize that i have windows xp on other partition, so it offer me the option to install grub, and i install it in MBR too... Then when the installation ends... and the machine reboot, this is what it show me:

GRUB loading...plase wait...

and stays there, dont do anything else...(in two times that I try)

What is the problem??? Can any one help me? it doesnt let my boot neither of my systems

---

### Post by adwait on 2005-07-13
Maybe you should have erased the GRUB b4 deleting the suse partitions. Anyway, if you have your windows recovery CD lying around, boot off it and use fixmbr or fdisk /mbr. Then reinstall Ubuntu (actually, just reinstall GRUB).

---

### Post by elmagozizou on 2005-07-13
thkz...that sove my problem...

---

