---
title: "Partition Question"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-02-20
My ext3 partition is 147 GB. I want to use 50GB as a separate backup partition. I have a GTParted DVD that I boot to and when I do the first step on the resizing it asks what I want to make that partition, fat32-ext2-ext3-and there are more. What I want is to leave it as ext3, will that be OK? 
Also, will the program give the new partition a new name or am I supposed to do that? I am hesitating because I don't want another disaster. I have a .tar backup of the system on my present ext3 partition and I do not want to loose that.

Any help greatly appreciated.

---

### Post by Patrick K on 2007-02-20
Unless you have a reason to use the backups with another OS, go with EXT3. 

GParted will give the new partition a new name. In addition, it might rename your existing partitions (happen to me). Make a note of any changes, particularly " / " since that is where the system boots from. If it renames your partitions, you may need to edit fstab to reflect this (I had to). 

If dual booting, and it renames "/", you will likely need to edit /boot/grub/menu.lst. But even before that you may need to edit grub directly at boot time just to get to Linux. To do this you select Linux and hit "e". Then you can edit the boot loader to reflect the changed partition names. This is a temperary fix, so edit menu.lst as soon as you are in Linux. Note also, that there are two different partition names used in grub. You will see, for example, hda1 (sda1 if a SATA drive) and hdd0,0. These are the same partition. The system BIOS uses hdd0,0 for what Linux calls hda1. Notice the partition number (the last number in the name) is one number lower in hdd0,0. conpared to hda1. 

If you have a /home partition, you may need to edit fstab if its name changed.

---

### Post by kindafunnylookin on 2007-02-21
Thank you, Patrick. I understand and will put this off until tomorrow and I might as well get a HOME partition going as well.
Peter

---

