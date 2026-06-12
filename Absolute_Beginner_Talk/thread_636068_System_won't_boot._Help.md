---
title: "System won't boot. Help"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Clintonostra on 2007-12-09
System won't boot. Help
When I first installed Gutsy it ran well prior to enabling the Restricted drivers, the system ran without lock-ups. After I enabled the Restricted drivers, then the lock-ups, freezes, and very absolute crashes began and the only way to get out of it was to do a hard reset and reboot.
Reinstalled Feisty but can't boot to it. The files are there and clean according to fsck before I receive a command line. I can read the files on the four partitions ( /, /home, /usr, /var) from my second disk.
Have Feisty on both disks, one bootable (sdb) ( 2.6.20-16) and one not (sda). Grub is included in the / directory.
This message could be of value: 	fsck.ext3: unable to resolve UUID. Then two UUID numbers are shown which belong to Gutsy which due not exist.
When I try to edit Grub, only Feisty shows for the two disks. On the live disk, ran root (hd0,0) and setup (hd0,0) with a grub prompt and received : error while parsing number. Also grub would not accept the command find /boot/grub/stage1.
Followed the forum instructions:
sudo -i 
mkdir /mnt/work
mount /dev/sda1 /mnt/work
mount -o bind /dev /mnt/work/dev
mount -o bind /proc /mnt/work/proc
cp /proc/mounts /mnt/work/etc/mtab
chroot /mnt/work/ /bin/bash
message:	groups: command not found
		dircoulors: command not found

Super GRUB disk didn't work. 
Looked at 5 threads that were shown when I started this thread.
Relatively new to Linx and any help would be most appreciated.

---

### Post by Mramius on 2007-12-09
What do you mean the supergrub disk didn't work?  Were you able to boot to it?

---

### Post by Clintonostra on 2007-12-09
Yes went through the procedures but it wouldn't enable my system to boot.

---

