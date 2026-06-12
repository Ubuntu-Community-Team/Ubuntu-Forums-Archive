---
title: "Refit 3boot problem. Neither Ubuntu or Windows will boot"
date: 2010-04-11
forum: Apple Hardware Users
---

### Post by jeppex on 2010-04-11
Hi all

Recently i reformatted my macbook and also installed Karmic and Windows 7. I use rEFIt to handle the boot.
In the start I experienced no problem using either, nor osx, besides an incredible slow boot for Windows. This seemed to be a problem with a bootloader for Windows, and I did this [http://www.dslreports.com/forum/r22969889-OS-X-Bootcamp-Windows-7-Ultra-Slow-Boot~start=20](http://www.dslreports.com/forum/r22969889-OS-X-Bootcamp-Windows-7-Ultra-Slow-Boot~start=20)

Which worked.
However, I'm not quite sure if I did anything specific, but all og a sudden Karmic wouldnt boot graphically. I installed the community supported drivers through Hardware Drivers, and were planning to install the newest drivers from NVIDIAs homepage.

I wanted to do that know, but now ubuntu wont even boot. After chosing the latest kernel in GRUB, it freezes at a black screen. Using the 'safety mode' (or what its called) I can see that it freezes right after saying
"EDD information not available"

Also, I cannot boot Windows, whick also freezes during startup (even if im trying to boot "startup repair")

OsX Snow leopard boots as it has always done, perfectly.

Anyone has any idea of what is going on?

Thanks!

---

### Post by linuxopjemac on 2010-04-11
You nuked Grub... I would reinstall Grub.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

btw you have Grub2

---

### Post by jeppex on 2010-04-11
Windows isnt booting through grub, but directly from refit.
And, when choosing linux in refit, grub still appear.

The new bootloader was installed directly to the windowspartition..

---

### Post by linuxopjemac on 2010-04-11
You might want to try the rEFIt's partition inspector.
[http://refit.sourceforge.net/help/linux_boots_windows.html](http://refit.sourceforge.net/help/linux_boots_windows.html)

---

### Post by jeppex on 2010-04-11
Thanks!

I tried that, however I have difficulties how to interpret the report. Ill post it here, maybe one of you can identity an error. The "MBR contents" seems flawed to me, though

```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    401305551  Mac OS X HFS+
 3      401567696    413288447  Basic Data
 4      413550592    488396799  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    401305551  af  Mac OS X HFS+
 3 *    401567696    413288447  83  Linux
 4      413550592    488396799  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 401567696:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 413550592:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS
```

---

### Post by jeppex on 2010-04-12
An update.
Both Ubuntu and windows seems to work on and of. Suddenly today, I was able to boot the newest kernel of ubuntu, and windows. 
Then I tried to install the latest version of the nvidia-driver from the recovery-version of the kernel only to find that when I typed a letter in the command line, it showed mostly squares instead. I suspect the reason is that I have cyrillic keyboard layout installed and that i chose that one as first priority. 
However, after forcing a physical reboot pressing the button, it wouldnt start up again afterwards.

I dont know really what the problem is, but the system us unstable.

---

