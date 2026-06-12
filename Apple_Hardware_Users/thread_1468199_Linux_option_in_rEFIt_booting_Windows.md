---
title: "Linux option in rEFIt booting Windows"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by Popple3 on 2010-05-01
I installed rEFIt, resized my Mac partition, created a FAT partition in the free space, booted into my Ubuntu 10.04 CD, and installed. However, it wouldn't let me install grub onto my Ubuntu partition (/dev/sda5 in this case), so I opted to not install it, then manually install it using the LiveCD. I mounted the partition and chroot'd into it, and installed. Installed fine, rebooted, "Missing Operating System" came up. Booted LiveCD, found there was no /boot/grub/menu.lst file, created it with a simple entry:
```
title Ubuntu
root (hd0,4)
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=b5e163b9-f63c-46f7-a902-af119e8ecc39
initrd /boot/initrd.img-2.6.32-21-generic
```
And now when I select Linux in rEFIt, it boots into Windows...
I've tried re-syncing the partitions in rEFIt, but it says they are in sync.

Any ideas how I can sort this?

System: MacBook5,1
OS: Mac OS 10.6; Windows 7; Ubuntu 10.04

EDIT: Got it sorted. I think the problem was that it was installed on an extended partition, and as a result wasn't showing up on the MBR in rEFIt.
So I deleted my ext4 (sda5) and swap (sda3) partitions, recreated them, doing the ext4 first so it would be sda3, and all is working well.

---

