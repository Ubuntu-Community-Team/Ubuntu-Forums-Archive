---
title: "Dual-boot - cant boot XP after dapper install"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by illadelphian on 2006-07-11
Here's my setup:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda2 /media/sda2 ntfs nls=utf8,umask=0222 0 0 defaults,nls=utf8 ,umask=007,gid=46 0 1
/dev/sda4 none swap sw 0 0

So i had my XP Pro 2006 install cd which I used to boot and repair my MBR. I still could not boot XP, just the dapper.

Then I dl'd GAG and created OS boot options, but I still couldnt boot XP. What I am confused about (may be a clue to you guys) is that when I used GAG to add XP using /dev/sda2....the ntfs...it actually would boot the dapper. And when I setup /dev/sda3 ...the ext3 to boot the dapper nothing would boot. I even setup up /dev/sda1...the fat32 to boot XP, but nothing happened. Why is the ntfs booting the dapper?

I had forgotten what GRUB was for a second when GAG came into the picture,,,haha. Anyway...when I installed the dapper I chose to install GRUB on my ubuntu partition and not the MBR. How can i confirm I did this?

I feel as if my problem has to do with XP not being activated. When I had installed GRUB to the ubuntu partition, I could not use QtParted in the System Rescue cd to get to my XP drive (/dev/sda2) to make it "set active." The program would hang when I selected the HD.

WHere is that GRUB file located to change the partition assignments u mentioned?

---

