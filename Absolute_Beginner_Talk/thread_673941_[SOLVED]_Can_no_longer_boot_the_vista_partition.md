---
title: "[SOLVED] Can no longer boot the vista partition"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by nikolas68 on 2008-01-21
Hey guys...i have Ubuntu installed as main OS (booting with Grub) and vista on another partition. Recently i needed more disk space for Ubuntu and i've re-sized the partitionings. Ever since i cannot boot vista: i get an error 13 system corrupted (cannot exactly remember how it goes LOL).
Although i never use vista....i still wouldn't mind having it....
Do you think that using the TestDisk application (never used before) could recover or fix the vista? Another thing: if i launch GParted, the NTFS partition is preceded by !

thanks for any help

---

### Post by bumanie on 2008-01-21
Test disk may work as it does deal with vista. I assume you altered partitions with gparted. Unfortunately, (unless things have changed recently) gparted does not work well with vista and any partitioning/resizing should be done with vista's native partition manager (I think it is an option under disk management).
Quoted from the GNU/GRUB manual
[grub error]13 : Invalid or unsupported executable format
This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).  

Are you trying to chainload a Linux partition by the boot sector? 
The first sector of a Windows partition is called the 'boot sector', and it has boot loader code installed there by default.
With Linux it is optional to have any boot code in the first sector of the partition and it isn't installed there by default in most distros. You have to install your bootloader to the partition yourself.
After you do that, then you can use the chainloader command and it should boot.

The chainloader command is the only way to boot Windows from GRUB.
One user reported receiving this error when trying to boot Windows and found the Windows bootsector had been corrupted somehow. TestDisk was used to repair the damaged ntfs bootsector and filesystem blocks enough to recover the data and Windows was re-installed. Using TestDisk for this could be overkill though.

The FIXBOOT command from a Windows recovery console would normally be the recommended way to repair a Windows bootsector and other files, but not all Windows users are able to access a recovery console easily. 

If it's a FAT32 file system in Windows you should be able to fix it from Linux. Run dosfsck -ar on it, refer to this link: When the bootsector is not the same as its backup
See site [http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13) for lots of grub info.

Try the FIXBOOT command in recovery console before trying test disk.

---

### Post by nikolas68 on 2008-01-21
Thanks for helping M8: i've used the TestDisk so far just to analyze and this is what i get in the .log

Current partition structure:
Invalid NTFS boot
 1 * HPFS - NTFS              0   1  1  3272 254 63   52580682
 1 * HPFS - NTFS              0   1  1  3272 254 63   52580682
 2 P Linux Swap            3273   0  1  3403 254 63    2104515
 3 P Linux                 3414   0  3 14592 254 63  179590633 [Ubuntu]


Was looking at the TestDisk website and they say: ...The first partition is listed twice which points to a corrupted partition or an invalid partition table entry,
Invalid NTFS boot points to a faulty NTFS boot sector, so it's a corrupted filesystem.

will try what you've suggested....let you know..

---

### Post by nikolas68 on 2008-01-21
thanks bumanie ....the fixboot worked:)

---

