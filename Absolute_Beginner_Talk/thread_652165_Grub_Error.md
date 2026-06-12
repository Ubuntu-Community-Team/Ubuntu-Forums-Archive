---
title: "Grub Error"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by mgaskell on 2007-12-28
Had to reinstall Windows and, of course, lost Grub. I've been combing the forums trying to fix the problem with no success. Booting from the live CD, I was able to reinstall Grub but when I reboot and select "Ubuntu, kernel 2.6.20-16-generic" I get Error 17: cannot mount selected partition.

When I select Windows XP from Grub I get looped back into the Grub boot menu.

My particulars:

I have one hard drive with three partitions:
sda1  is the NTFS Windows partition
sda2 is the ext3 Ubuntu partition
sda5 is the linux swap partition

What I've already tried:

From the terminal after booting to the live CD
sudo grub
find /boot/grub/stage1 - this returned (hd0,1)
root (hd0,1)
setup (hd0)
quit

Rebooted with same problem

I then tried the same steps substituting setup (hd0,1) in the 4th step - no good.

I then entered these steps in the terminal before trying to reload grub:
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda2 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)
quit

Same problem - cannot get into Ubuntu or Windows from Grub.

I figure there is a configuration file somewhere that needs to be edited but I need help there.

Thanks in advance

---

### Post by PriceChild on 2007-12-28
*moved and approved*

---

### Post by spiderbatdad on 2007-12-28
/boot/grub/menu.lst contains locations of the kernel on the disk. You probably know that. But you might be able to confirm the sectors.

---

### Post by dstew on 2007-12-28
Your problem is not with the grub installation but with the menu.lst file, and/or drive mapping. You can tell this because the menu appears, and your error comes with an explanation "cannot mount selected partition". If grub had not been installed correctly, it would not be able to find its stage 2 file, and you would only get the error number, with no comment. This explanation comes from grub stage 2. So, you have installed it correctly.

We can try to fix the menu.lst file. Post to the forum the output of the commands:```
sudo fdisk -l
cat /boot/grub/device.map
cat /boot/grub/menu.lst
```

---

### Post by eternicode on 2007-12-28
The Grub menu config file is /boot/grub/menu.lst

Have you tried pressing "e" in the grub menu and looking at the details for each boot item?  That may give you some hint as to what's wrong.

Have you tried running "grub-install /dev/sda" from the live environment, or is that what you did to reinstate it in the first place?

---

### Post by meierfra on 2007-12-28
mgaskell already solved  the  problem:

[http://ubuntuforums.org/showthread.php?t=224351&page=4#272]("http://ubuntuforums.org/showthread.php?t=224351&page=4#272")

---

