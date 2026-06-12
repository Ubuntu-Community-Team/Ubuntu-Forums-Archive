---
title: "Triple boot: Wish to install Mint 13, Solus OS along with Windows XP!"
date: 2012-07-12
forum: Any Other OS
---

### Post by saad1gamer on 2012-07-12
hi everyone,


I have a core 2 duo PC with 2 GB ram and ATI graphic card. I already have Windows XP installed on the PC. I also wish to install 32 bit 1- Linux Mint 13 and 2- Solus OS 1 while keeping Windows XP default for the time being. Kindly inform me how to do that? Also how much space should I give to each distro? 


Following is my current hard disk partition set up:


C: 62.1 GB (Has Windows XP)

D: 62.1 GB (Has Windows Data)

E: 62.1 GB (Free)

F: 74.5 GB (Another hard drive - Free)


Kindly guide me how to do that since I am not an expert I need your help. Best regards. :)

---

### Post by CrocoDuck on 2012-07-12
Hi. You could act like this: 4 GB of swap partition and 2 root partitions for each linux installation. To do it, start installing one (for example Mint). When the install program asks for partitions choose "manual specification" (or similar) and create the swap partition and a ext4 partition (as big as you want, remember that you have to left free space for Solus OS) with the / mount point. Once finished installation install the second one (Solus OS in our example) in a ext4 root (/ mount point) partition big as you want created in the remaining free space. You could also left some free space in order to create a partition to store common linux datas. Set the filesystem vfat or fat if you want windows operative on it. Once finished login in Solus OS and edit GRUB in order to have Windows on default [http://www.danbishop.org/2011/05/26/make-windows-the-default-operating-system-in-grub2-even-after-ubuntu-updates/](http://www.danbishop.org/2011/05/26/make-windows-the-default-operating-system-in-grub2-even-after-ubuntu-updates/).

---

