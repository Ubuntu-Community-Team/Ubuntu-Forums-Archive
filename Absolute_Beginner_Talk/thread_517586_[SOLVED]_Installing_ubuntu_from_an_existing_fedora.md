---
title: "[SOLVED] Installing ubuntu from an existing fedora core 5 os"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by lyeandro on 2007-08-04
Considering im giving up with my yum repomd.xml errors,i tried to switch from fedora core 5 to ubuntu 7.04. I have an existing windows partition as well as fedora core 5 all set for dual boot. 

Im a newbie in linux world so im asking if is it possible not to affect my bootloader just in case i tried to install ubuntu erasing my fedora without harming my windows?:confused:

---

### Post by apswartz on 2007-08-04
If I understand you correctly, you want to...
1. remove Fedora
2. keep Windows
3 add Ubuntu

If that is right, then yes you can do it. When you install Ubuntu, you can tell the installation program to delete the partitions used by Fedora, install Ubuntu, and it should set up a bootloader (grub) that will give you the choice of Windows or Ubuntu.

---

