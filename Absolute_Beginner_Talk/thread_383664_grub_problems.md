---
title: "grub problems"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by wannabuntu on 2007-03-13
Hi there,
            I installed windows vista on my pc and now i cant get my beloved ubuntu back :confused:

I've tried super grub but i cant get my grub back and booting with ubuntu. I'm a novice so i dont know how to use the advanced features of Ubuntu. 

if i will have to reinstall...can i get my files which i had in ext3 drive back????

better still is there a way of getting grub back???

---

### Post by dstew on 2007-03-13
Unless you deleted your ext3 partition, you should only need to re-install grub. To make sure your ext3 partition is still there, boot from the Ubuntu live CD, and open gparted. It will display your partitions.

If the linux ext3 and swap partitions are still there, all you need to do is re-install grub. From a liveCD desktop, open the terminal and start grub. At the grub prompt type:

grub>find /boot/grub/menu.lst

The output will give the name of the partition that your linux system boot menu is on. Use this answer and make it grub's root using:

grub>root (hd0,1)

or whatever the result happens to be. Then, install the grub boot loader into the master boot record of your first disk, which is probably your windows disk:

grub>setup (hd0)

Quit grub and reboot without the live CD. If you get the grub menu, but it still won't boot properly, you may need to edit your /boot/grub/menu.lst file.

---

### Post by wannabuntu on 2007-03-13
Thanks for the help!!!:) will try it out now.

---

### Post by Najand on 2007-03-13
Probably dstew's explaination will help, but use the following documentation if it doesn't: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

