---
title: "rEFIt doesn't work"
date: 2010-08-04
forum: Apple Hardware Users
---

### Post by sfresta on 2010-08-04
Hi guys,

I just installed kubuntu 10.04 on my macbook santarosa (4.1 version, Dual Core 2.4 GHz) and all seems to work (wifi, isight, audio, sound etc.). I formatted the entire hard disk using the ext4 filesystem:

/dev/sda1 as boot with ext4
/dev/sda2 as swap 
/dev/sda3 as root with ext4

I noticed that when I reboot the system, grub doesn't start immediatly (the screen remains in gray) but after few seconds (about 10) without the classic bootloader image and without the menu.

I tried to install refit to boot from external devices but it doesn't seems work. If I insert the cdrom on the drive and reboot, it will be ejected.

I tried also gptsync:

sudo gptsync /dev/sda

Current GPT partition table:
 No GPT partition table present!

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1 *         2048       585727  83  Linux
 2         585728      2539519  82  Linux swap / Solaris
 3        2539520    312580095  83  Linux

Status: No GPT partition table, no need to sync.

How to solve? I can't do a boot from an external device because it doesn't start :-(

Regards.

---

