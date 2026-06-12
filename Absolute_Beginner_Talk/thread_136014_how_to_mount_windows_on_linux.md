---
title: "how to mount windows on linux"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Kunalsoni on 2006-02-25
hi everyone!
I am a new user I have just installed linux on my PC.I also have windows as other operating system,I chose do not use option for two of the patitions one with ntfs and other with the fat32 with (/windows mount points)file system while installing the linux.Now I want to use those drives through linux.

PLease someone tell me how to access those drives now?

---

### Post by desheikh on 2006-02-25
Hi,
You need to use the mount command:
create a folder where youd like the partition to be mounted and type something like this

mount -t ntfs(or vfat for fat32) \dev\hda1(replace with whatever your device name is) \windows\c_drive(folder where you want to mount the partition)

If you want them to be mounted on boot you should add the respective command in \etc\fstab

[http://linux.about.com/od/commands/l/blcmdl8_mount.htm](http://linux.about.com/od/commands/l/blcmdl8_mount.htm) if you need more info

Ali

---

### Post by sas on 2006-02-25
Hi, 
If the files are already mounted you should be able to browse to them by clicking on the "places" menu, then "computer", then "filesystem", then navigating to the /windows mount point, failing that you could check the /media mount point.

If they're not in either of those places then reading [http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html) may help.

If you can't get it working could you copy the contents of the /etc/fstab file to t?he forums

---

### Post by aysiu on 2006-02-25
[QUOTE=sas]
If they're not in either of those places then reading [http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html) may help.[/QUOTE] That tutorial is correct but incomplete. 

For example, it doesn't tell you how you would know whether your FAT32 partition was /dev/hda1 or /dev/hda2 (or /dev/hda3, etc.). It links to something about viewing the partition table... close, I guess.

It also doesn't mention there should be only one entry per partition in /etc/fstab--it says simply to *add* a line for it. In Breezy, there usually already exists a line for that partition. 

Lastly, it doesn't tell you that in order for the changes to take effect, you have to remount the partition.

See the fourth link of my signature instead. If you have questions afterwards, post them here, and we'll try to help out.

---

### Post by sas on 2006-02-25
[QUOTE=aysiu]That tutorial is correct but incomplete. 

For example, it doesn't tell you how you would know whether your FAT32 partition was /dev/hda1 or /dev/hda2 (or /dev/hda3, etc.). It links to something about viewing the partition table... close, I guess.

It also doesn't mention there should be only one entry per partition in /etc/fstab--it says simply to *add* a line for it. In Breezy, there usually already exists a line for that partition. 
[/QUOTE]
You're quite right, could you file a bug on the 'ubuntu-doc' package? I'll try to do something about that if I have time, though patches are always welcomed if you'ld like to help out though? See: [https://wiki.ubuntu.com/DocumentationTeam/GettingStarted](https://wiki.ubuntu.com/DocumentationTeam/GettingStarted)

[QUOTE=aysiu]
Lastly, it doesn't tell you that in order for the changes to take effect, you have to remount the partition.
[/QUOTE]
The last step of each procedure in the guide says "read 'how do i remount with rebooting'", surely that makes it quite clear?

---

### Post by sas on 2006-02-25
Actually upon rereading it, it tells you to use disks-admin, which is more obvious than 'mount' and more friendly than fdisk -l. It just needs to mention which filesystem it is.

---

