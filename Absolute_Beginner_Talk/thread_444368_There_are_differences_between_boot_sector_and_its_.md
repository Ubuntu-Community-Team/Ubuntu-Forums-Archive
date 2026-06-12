---
title: "There are differences between boot sector and its backup."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-05-15
I keep getting this error on boot. It takes forever to boot, and i think it's because of this error. Can anyone help me?

** more /var/log/fsck/checkfs**

Log of fsck -C -R -A -a 
Tue May 15 14:55:24 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00
  Not automatically fixing this.
/dev/evms/hda5: 19 files, 20/2024290 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/evms/hda1: 58584 files, 980577/1412524 clusters
/dev/evms/hda3: clean, 960/732960 files, 76547/1465931 blocks (check after next 
mount)

Tue May 15 14:56:12 2007
----------------

---

### Post by EXCiD3 on 2007-05-15
What this means is that you have changed GRUB at one point in time. When Ubuntu is installed, it makes a backup of the MBR (Master Boot Record) GRUB installs to this which allows you to boot your computer. If you have a corrupt MBR, you cannot boot. This is very important and Ubuntu warns you that it has been changed. Most likely you may have changed the default OS or the colors or something along these lines. You should not have to worry about this unless GRUB doesn't work anymore.

---

### Post by Herman on 2007-05-15
Hello Pulka,
[                      When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup")
[the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#the_bootsector_is_not_the_same_as_its").
Try those two links and see if they help you,
Regards, Herman:)

---

