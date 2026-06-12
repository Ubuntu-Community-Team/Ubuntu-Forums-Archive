---
title: "[SOLVED] Tribooting with Arch"
date: 2008-02-27
forum: Arch and derivatives
---

### Post by ep2011 on 2008-02-27
Right now I have ubuntu and windows installed. I have the following partition layout:

/dev/sda1 - HP Restore Partition
/dev/sda2 - Windows XP
/dev/sda3 - Extended
/dev/sda4 - ubuntu /home
/dev/sda5 - linux swap
/dev/sda6 - ubuntu /

If I wanted to resize both my /home and windows partitions, and install arch, how would I do grub? would I not install it in the arch install process and then add the entry to the ubuntu grub? I've never installed anything but ubuntu, so easy to read instructions would be great... thanks :)

---

### Post by jeffus_il on 2008-02-27
Download "Supergrubdisk" and burn it, keep it handy in case you run into booting problems. It should save you a lot of headaches...

---

### Post by Rumor on 2008-02-27
> **ep2011 said:**
> 
If I wanted to resize both my /home and windows partitions, and install arch, how would I do grub? would I not install it in the arch install process and then add the entry to the ubuntu grub? I've never installed anything but ubuntu, so easy to read instructions would be great... thanks :)

If you wanted to triple boot, give yourself some space for Arch to install / and /home. I recommend doing so with the gparted live cd. make certain you write down the names of the new partitions you've made so you can use them for your Arch install.

While you are installing Arch, you'll come to the disk preparation stage. you'll want to select file system mount points for your new partitions.

Let the install process do your base install as normal.

When you come to the step to install grub, make certain you do one of two things. 
1) While you are previewing Arch's grub entry, copy the relevant bits down and then do not install the bootloader. When you reboot into Ubuntu, edit Ubuntu's grub menu.lst and add the entry for Arch, reboot and boot into Arch. Or:
2) Install grub to the / partition for Arch. Boot into Ubuntu, browse to the / partition for Arch, copy the entry and paste it into your Ubuntu grub menu.lst file.

I know neither of those solutions are the most elegant, but they are what I did when I was dual booting Ubuntu and Arch.

---

### Post by ep2011 on 2008-02-27
> **Rumor said:**
> If you wanted to triple boot, give yourself some space for Arch to install / and /home. I recommend doing so with the gparted live cd. make certain you write down the names of the new partitions you've made so you can use them for your Arch install.

While you are installing Arch, you'll come to the disk preparation stage. you'll want to select file system mount points for your new partitions.

Let the install process do your base install as normal.

When you come to the step to install grub, make certain you do one of two things. 
1) While you are previewing Arch's grub entry, copy the relevant bits down and then do not install the bootloader. When you reboot into Ubuntu, edit Ubuntu's grub menu.lst and add the entry for Arch, reboot and boot into Arch. Or:
2) Install grub to the / partition for Arch. Boot into Ubuntu, browse to the / partition for Arch, copy the entry and paste it into your Ubuntu grub menu.lst file.

I know neither of those solutions are the most elegant, but they are what I did when I was dual booting Ubuntu and Arch.

Okay, thanks. Answered my question perfectly with very simple steps :)

---

