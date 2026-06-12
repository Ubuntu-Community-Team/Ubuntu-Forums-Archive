---
title: "Have Maverick: Want to multi-boot Ubuntu + Fedora + OpenSUSE"
date: 2011-05-12
forum: Any Other OS
---

### Post by 3602 on 2011-05-12
Sorry but I do not know whether this is better suited here or at the Ubuntu main boards.
Well... Basically how? Any manual repartitioning or Grub fixing? I am sorry but I do not know how I can elaborate my questions...
 
Thank you very much.
 
EDIT: Well there's VM, I already tried Mandriva with VBox, so I guess...

---

### Post by garvinrick4 on 2011-05-12
You will be partitioning through a package called "gparted" to make a partition for 2 more
installs. You will be using a graphic installation package called "anaconda" for fedora and OpenSuse both use grub-legacy do not install grub at all use Ubuntu's grub2 to boot off of. So do not install GRUB AT ALL. Boot into ubuntu when done and "sudo update-grub" will put fedora and or OpenSuse in menu entry and grub-config. You will use RPM package management for repositories in both. Fedora uses yum instead of apt-get and OpenSuse uses zypper instead of apt-get. So there are some items you can google and study first. Here is a few links. Enjoy 

[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 
[Fedora 14 Laughlin – Reference Cheat sheet]("http://digitizor.com/2010/11/03/fedora-14-cheatsheet/")
[Fedora 12 Installation and Post Installation Guide - my-guides.net]("http://www.my-guides.net/en/guides/linux/174-fedora-12-installation-and-post-installation-guide")
[Main Page -]("http://ubuntuguide.org/wiki/Main_Page")

---

### Post by 3602 on 2011-05-12
That's cool. I'll keep Grub in mind.
So what partitions should the new ones be? Ext3? Ext4? Definitely not NTFS that I understand...

Thanks.

---

