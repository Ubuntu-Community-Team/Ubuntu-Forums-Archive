---
title: "Removing Ubuntu from slave drive and...."
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by lowercaserick on 2006-08-05
I want to remove Ubuntu from a slave hdd that I have installed and I want that hdd to be reformatted so it can be used by Windows again.  I've been unable to find a way to do this normally, and I'm not able to access the internet with ubuntu to download any programs and could use some help.  I tried Ubuntu and I'm just not experienced enough with computers to migrate to a completely foreign system.  Thanks in advance.

---

### Post by OU812 on 2006-08-05
I think the livecd has either qtparted or gparted. You can use that to format the drive. Maybe format it as fat32 so win can "see" the drive next time you boot to win. Then keep it as fat32 or reformat it in ntfs using win. There may be other ways, this just came to mind first.

john

---

### Post by lowercaserick on 2006-08-06
> **OU812 said:**
> I think the livecd has either qtparted or gparted. You can use that to format the drive. Maybe format it as fat32 so win can "see" the drive next time you boot to win. Then keep it as fat32 or reformat it in ntfs using win. There may be other ways, this just came to mind first.

john

How would I access g or qparted?  Sorry, I'm truly a Linux noob.

---

### Post by confused57 on 2006-08-07
If grub is installed on the Windows mbr and you "uninstalled" Ubuntu from your slave drive, you wouldn't be able to boot Windows.
You need to repair the Windows mbr using the Windows XP installation CD(not the recovery CD)...bootup with the CD, press "r" to enter recovery mode, then enter *fixmbr*...this should restore your Windows mbr, but you wouldn't be able to boot Ubuntu.  If you don't have the Windows install CD, you can use a Win98SE boot disk:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You should be able to reformat the slave drive from Windows, or download the Gparted LiveCD(approx. 30 mb) and reformat the drive as FAT32(or NTSF?)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by OU812 on 2006-08-07
Doh - I completely forgot about that. In fact, I just had that very problem when I tried to replace my drive (with ubuntu on it) with a bigger capacity drive. Thanks for catching my mistake.

john

---

