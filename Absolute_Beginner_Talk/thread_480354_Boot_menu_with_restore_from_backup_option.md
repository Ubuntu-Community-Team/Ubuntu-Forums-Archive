---
title: "Boot menu with restore from backup option"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Padakwaak on 2007-06-21
Hi, how do I create a boot menu to give me the options:
1) boot OS (default, Windows/Linux)
2) restore OS to previous state (from image/backup file/partition)

My situation is: I have a system on which I test drivers and applications that can damage the OS and then the PC should have an option of quickly restoring the OS from a backup. The solution should accomodate both Windows and Linux installations (only 1 per PC) and it must be able to run without booting from USB/CD.

Currently I'm stuck at the automation & creation of the boot menu.
I've experimented with a Parted Image 1.7 LiveCD to create and restore backups using either the partimage or clonentfs application. For both Windows XP and Windows Vista I created the backup image using:
```
ntfsclone --save-image -o - /dev/sda1 | \
gzip -c > backup.img.gz
```and restored the image using:
```
gunzip -c backup.img.gz | \
ntfsclone --restore-image --overwrite /dev/sda1 -
```
The system I'm doing the testing on current has 1 harddrive with 2 partitions: 1 for the OS and another for the backup.
I'm fine with the creation of the backup, because it's only going to be done once after the OS is running and stable.

My solution would've been something like:
1) creating a new Linux partition on which I was going to copy a remastered version of the Parted Image ISO so that it's only able to boot and then automatically restore the backup
2) installing GNU Grub bootloader to give let the user choose between booting the OS and restoring the backup
I'm not even sure if this would be possible since my knowledge of Linux is quite limited.

Any ideas/suggestions would be appreciated!

---

### Post by Padakwaak on 2007-06-21
Instead of going through all of the stuff I mentioned above, one of my friends proposed to me that I should rather install a minimal version of Ubuntu onto a new partition which I will in turn use to store the backups too.

Where/how do I only install Ubuntu with ONLY ntfs-progs and partimage packages along with its dependencies? I came across some minimal Ubuntu installation ISO's @ [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) 
Also, how do I modify that when my Ubuntu boots (already installed) that it automatically restores the backup by executing the ntfsclone commands like I mentioned above?

---

### Post by Padakwaak on 2007-06-22
OK, I've managed to:
1) install Ubuntu from minimal CD
2) install ntfs-3g, partimage & ntfsprogs packages with sudo apt-get install commands
3) change the GRUB bootloader menu @ /boot/grub/menu.lst
4) add 2 commands to the local startup script @ /etc/rc.local

Now my question is: since my rc.local file contains "reboot" as the 2nd-last command, how do startup my linux without it rebooting/executing the rc.local script? Is there a better way than just using a LiveCD like Knoppix or so?

---

