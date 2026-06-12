---
title: "Operating System not found"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by dylan_craven on 2007-12-17
hi,

i was not able to unmount an external hard drive last night, and as i was rushing out of the office, i unplugged the device and had to force quit in order to shut down. later in the evening i tried to restart the computer, and i received the " operating system not found "  message after the initial start up screen (ie could not enter grub).  i had experienced a similar problem before with a media device, so i tried entering the bios to switch the boot order of devices (ubuntu likes to make the last unmounted device the boot). i tried to boot from every device on the list... and stil ubuntu will not load.

i went toi ubuntu forums and checked out various links which suggested using a live cd to boot.

i got this message, upon initiating the live cd i received the following messages:  
(initramfs)  buffer i/o error  on device hda, logical block 0

[there were a few of these]
then:  idm_validate_partition_table(): disk read failed

then:  more of buffer i/o error on device hda, logical block (various locations)


ANY help would be greatly appreciated

---

### Post by philinux on 2007-12-17
if the external drive is formatted ext2/3 you could run fsck on it. If it's vfat or ntfs you could run check disk.

---

