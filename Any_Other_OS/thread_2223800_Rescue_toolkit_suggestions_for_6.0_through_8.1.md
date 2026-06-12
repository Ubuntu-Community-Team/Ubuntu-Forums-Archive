---
title: "Rescue toolkit suggestions for 6.0 through 8.1?"
date: 2014-05-13
forum: Any Other OS
---

### Post by bcschmerker on 2014-05-13
I am currently developing a plan to set up a new 1 TB Western Digital® server-grade SATA drive (in for the stock Seagate® ST31000528AS due to an identified thermal issue) as the new /dev/sda in my Asus® CM1630-06 with EAH6850 DirectCU® video, XONAR® Essence™ audio, and Antec® power. Extrapolating from the recommendations from the Microsoft® Developer Network™, I'm preplanning seven sub-partitions of one extended GUID partition /dev/sda1 (marked as Type 0xee in the master boot record) for all but the last one or two Cylinders of the new drive. All extended subpartitions of sda1 will be NTFS (unless Sun Microsystems ZFS has been demonstrated to run properly in Windows® Server™ 2008-up); except sda5 (WinRE) and sda7 (GPT, mounted as C:\Boot) will be FAT32 for BIOS compatibility, and sda6 (OEM) potentially either ext4 or btrfs to contain an offline-repair toolkit running under a local-build LinUX Kernel 3.14.0. When running, I anticipate sda9 (WIN_7, mounted as C:\) and sda10 (USER, mounted as D:\) being routinely used; sda8 (MSR) will handle swap duties, and sda11 (FACTORY) will be held in reserve for an OEM-restore function.

I have had mixed success to date with LinUX offline tools for Windows® NT™ dealing with issues in the existing installation, as the open-source community's knowledge of User-data, -metadata, and -passphrase hash formats used in C:\Windows\SysWOW64\SAM.reg and certain other system datafiles is limited. However, basic NTFS tools have demonstrated their worth in fixing some critical items. Perhaps some of our more savvy dual-booters have some recommendations for offline tools that will run in LinUX 3.14?

---

