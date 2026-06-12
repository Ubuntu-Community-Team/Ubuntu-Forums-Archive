---
title: "Backup system and home to another HDD"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-03-20
Hello, I have Ubuntu 7.10. There are 2 partitions, one is root and other is home.
I have another HDD connected to the system, 250 Gb and mounted as /BackupDisk.
Every month, I use SystemRescusCd and take an image, using PartImage, to the BackupDisk. I also use "Simple Backup" to backup my /home folder to the BackupDisk. My questions are:
1) The "Simple Backup" config also includes some folders like /var, /usr/local, /etc by default and excludes MP3 and Media files. Does this mean that my MP3 and Video files in home folder are also excluded?
2) Since I take an image of the root partition using PartImage, can I remove folders other than /home from "Simple Backup"? Or should I let them be?
3) Should I partition my other HDD, would it give any benefits?
4) Should I use the Loagrithimic Purging of "Simple Backup"? It seems to keep very old backups.
5) The Gz file made by "Simple Backup" doesn't seem to open easily, maybe as it is 3Gb in size. Any software to open and view it fast.

---

### Post by jesrani on 2008-03-20
I have to add another question:
1) In case of a HDD failure, will I be able to restore my Image and home partitions from the backups I have created, does this method seem ok?

---

### Post by Tews on 2008-03-20
The best solution that Ive found is Quick Start .. This app will . 

1. Install the proper DVD & Codecs files so you can play a DVD in your drive using Totem, etc. (works with 7.10 / 7.04 and 32-bit / 64-bit).

2. Back-up Your /home folders

3. Back-up Your / folders

4. Back-up Your Configuration files separately (fstab, device.map, mtab, menu.lst, and xorg.conf)

5. Create a Custom Back-up for selected folders

6. Create a Custom Scheduled (Recurring) Back-up (daily, weekly, or monthly). You decide the exact date and time

7. Create a Scheduled 1:1 Synchronized Back-Up of Selected Folders to Another Drive/Partition.

8. Restore Your System /home folders

9. Restore Your / folders

10. Restore Your configuration files

11. Install some common applications (aMSN, aMSN fix, Firestarter, AllTray, and a few others). Nice when you're starting from scratch (clean install)

12. House Cleaning (delete unnecessary files throughout your computer).

13. View or Edit Your Key Files (fstab, menu.lst, and xorg.conf).

14. Back-up Your Master Boot Record (MBR).

15. Back-up Your Windows Partition (dual booters) While in Ubuntu.

16. Format Windows Partition in NTFS with gParted.

17. Restore Your Master Boot Record (MBR).

18. Restore Your Windows Back-Up While in Ubuntu.  

19. Download Updates/Upgrades with a click of the mouse.

You can read more about it here ... [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

---

