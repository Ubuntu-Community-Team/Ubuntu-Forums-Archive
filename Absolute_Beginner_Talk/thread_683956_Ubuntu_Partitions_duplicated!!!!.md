---
title: "Ubuntu Partitions duplicated!?!?!?!"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by wolterh on 2008-01-31
Hi. yesterday I installed Ubuntu on my pc, and today I look at the partitions with partition magic and I see 2 swap (exactly the same size) and 2 ext3 (exactly the same size too)
Also, Is it possible to install applications directly on a hard disk? Is that I have a dual boot, and the partitions I made for ubuntu are very small, and I can't make them bigger I dont know why. So I plan installing my applications on the drive that windows uses...

---

### Post by dannyboy79 on 2008-01-31
> **woli said:**
> Hi. yesterday I installed Ubuntu on my pc, and today I look at the partitions with partition magic and I see 2 swap (exactly the same size) and 2 ext3 (exactly the same size too)
Also, Is it possible to install applications directly on a hard disk? Is that I have a dual boot, and the partitions I made for ubuntu are very small, and I can't make them bigger I dont know why. So I plan installing my applications on the drive that windows uses...

you really should post the output of the following files so we can remove the unneeded partitions adn clean this up. you don't want to mount your windows drive and install apps on that. in fact I don't even think that'll work because when you use synaptic, it puts the programs in a pre-determined location. /usr/bin/ etc etc.

paste the contents of each of these file and or commands run in a terminal session.

/etc/fstab

sudo fdisk -l

/boot/grub/menu.lst

also, inform me of where you installed ubuntu to, example, if sudo fdisk -l shows /dev/sda1 and /dev/sda2, you would look in each of the folders within /media/ and see which one has folders in it, for example: /boot/, /etc/, /home/. that's the one where you ubuntu is and we need to leave that one alone.

once you post the neccessary info, I can help you clean it up after rebooot your system into a livecd.

---

### Post by wolterh on 2008-02-01
Well, nevermind. I formatted my hard drive.

---

