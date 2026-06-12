---
title: "Can't run Ubuntu on dual boot Linux/WinXP"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by RobCai on 2006-07-16
Hi I'm trying to install Ubuntu (Breezy Badger) on the following computer hardware configuration:

c: Primary HD (80GB): Win XP Pro (NTFS)
d: Secondary HD (80GB): NTFS
g: Primary SATA (160GB): Ext3-Ubuntu (25GB), SWAP (5 GB),  FAT32 (1GB), NTFS (Remaining GBs)

On my first run I loaded GRUB onto the MBR and got an "Error Loading Operating System" on bootup which I had to fix with the WinXP Recovery fixMBR

I then tried loading GRUB onto the boot sector of the linux install (sda) and copying a linux.bin to my Win XP root directory and altering the boot.ini file. Now I get the GRUB menu on boot-up. Clicking Ubuntu, I get Error 15 (HD2,2) partition does not exist. Clicking on Win XP returns me back to the GRUB menu. Bypassing the menu and loading from the Primary hard drive gets me the Windows boot.ini XP/Ubuntu option. Windows loads OK but the Ubuntu options just blinks.

Running grub>find /boot/grub/stage1 from the Live CD answers (hd2,2)

I have a Dell 4600 - the BIOS does not give me many options (e.g. cannot force Primary HD to boot before SATA, can't find any LBA settings)

I can bypass the GRUB menu on boot up by deactivating the ext3 partition from Win XP

Any help would be greatly appreciated!
Regards Rob

---

### Post by Emceay on 2006-07-16
Have you tried pressing 'e' on your ubuntu option in grub and trying different drive/partition combos? I had that same issue and it didn't work until I changed (HD2,1) to (HD1,1)
Doesn't make much sense since ubuntu was the second drive for me, but it's what ubuntu wanted me to change in order to work.

---

### Post by deadgobby on 2006-07-16
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)
 A great how to vid on line. What more can you ask for.

---

