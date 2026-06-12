---
title: "Need to get files from windows partition"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by banjosarecool on 2007-05-12
Hi, I just installed ubuntu 3 days ago and am completely new to linux systems.   I need to go back on my windows partition to get some of my music, pics etc.  However, when I restart the computer and tell it to start in windows it just goes to a screen that says "Starting up ..." and stays there until i turn off the computer and reboot it in linux.  What am i doing wrong?

---

### Post by jfinkels on 2007-05-12
> **banjosarecool said:**
> Hi, I just installed ubuntu 3 days ago and am completely new to linux systems.   I need to go back on my windows partition to get some of my music, pics etc.  However, when I restart the computer and tell it to start in windows it just goes to a screen that says "Starting up ..." and stays there until i turn off the computer and reboot it in linux.  What am i doing wrong?

If you can't boot into Windows, you can mount the partition from Ubuntu and access the files that way.

If it's an NTFS formatted partition, you can access the files using the NTFS-3G driver and ntfs-config.

Enable the universe repository in "System > Administration > Software Sources". Then type the following command:```
sudo aptitude install ntfs-config
``` Once that is installed, type the following: ```
gksudo ntfs-config
``` and you will be taken through a 'wizard' that will help you to mount your Windows partition.

EDIT: Fixed as per jiminycricket's comment below; thanks.

---

### Post by jiminycricket on 2007-05-12
just make sure to use either kdesu or gksudo with graphical apps like ntfs-config.  [https://help.ubuntu.com/community/RootSudo#head-0c932eb3f1619126fc8307ee7690f462552d34ec](https://help.ubuntu.com/community/RootSudo#head-0c932eb3f1619126fc8307ee7690f462552d34ec)

---

