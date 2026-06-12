---
title: "fstab doesn't show mounted disks (even though they clearly are mounted)"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by loldrup on 2008-02-16
Isn't /etc/fstab supposed to show which things are mounted where?
I can access my USB disks via Nautilus, but I can't see them in fstab.

My real problem:
I have an external usb-disk that automounts to /media/backup
For some reason, it has lately been mounted to /media/backup_ which has confuses my backup application (sbackup)
What is even more weird is that /media/backup still seems to exist - but I don't have two backup-disks - how can I see both /media/backup and /media/backup_ at the same time? They even have different content.. :shock:
The /media/backup and thing cannot be my second USB-disk, as that has some totally different content.
I hope some of you guys can help me shed some light on this case.

---

### Post by Hendronicus on 2008-02-16
If you want to see where all volumes are mounted, all you have to do is open a terminal and enter the command "mount" without the quotes.

---

### Post by loldrup on 2008-02-16
This command doesn't show whats mounted on /media/Backup either:

jon@jon1:/media$ sudo mount | grep /media/Backup
/dev/sdc1 on /media/Backup_ type ext3 (rw,nosuid,nodev)


This is the content of /media/Backup_  :
1946                                 2008-02-02_06.00.01.808166.jon1.inc  2008-02-05_06.00.03.994581.jon1.inc  Manuelle Backups
2008-02-01_01.26.35.224627.jon1.ful  2008-02-03_06.00.02.319256.jon1.inc  autoBackups
2008-02-01_06.00.03.860692.jon1.inc  2008-02-04_06.00.04.225223.jon1.inc  lost+found

This is the content of /media/Backup   :
2008-02-06_06.00.02.000501.jon1.ful  2008-02-10_06.00.01.411663.jon1.inc  2008-02-14_06.00.01.506457.jon1.inc
2008-02-07_06.00.01.491443.jon1.inc  2008-02-11_06.00.01.527774.jon1.inc  2008-02-15_06.00.03.475192.jon1.inc
2008-02-08_06.00.02.608713.jon1.inc  2008-02-12_06.00.02.158051.jon1.inc  2008-02-16_06.00.03.632629.jon1.inc
2008-02-09_06.00.03.292909.jon1.inc  2008-02-13_06.00.03.007299.jon1.inc  autoBackup

---

