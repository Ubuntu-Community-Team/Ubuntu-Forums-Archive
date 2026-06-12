---
title: "Windows 7 won't load after shrinking/ partitioning HDD"
date: 2013-05-07
forum: Any Other OS
---

### Post by Dnzeka on 2013-05-07
Greetings my fellow Ubuntu users!

I have been using ubuntu for the past couple of years and I love it! But due a lot of software being exclusive to Windows, I have been trying to dual-boot with Windows 7.

I first created a live usb for Windows 7 using Unetbootin. I restarted the pc, but me being a total n00b I didn't realize l needed to format & partition my HDD first. So I shrunk my Linux partition to about 180gb & formatted/ created a 275gb NTFS partition to install Windows 7. 

But once I created the partition the Windows installation CD would not run and keeps giving me the error 0xc000000f

I'm really a n00b when it comes to this kind of stuff so I would really appreciate it if someone could help me out of this jam!

---

### Post by oldfred on 2013-05-07
Is your NTFS partition a primary partition (sda1 thru sda4) with the boot flag?

Windows only installs to primary partitions. And it usually is better if the extended partition is not before the Windows. Windows has been know to corrupt partition tables as it does not see the Linux partitions in the extended partition. 
Some may say Windows needs to be first but that is not required, but since Windows is usually on new systems it is how most have it.

 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You will need liveCD, DVD or flash drive to reinstall grub2 to MBR. Windows will just install its boot loader to the MBR.
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

