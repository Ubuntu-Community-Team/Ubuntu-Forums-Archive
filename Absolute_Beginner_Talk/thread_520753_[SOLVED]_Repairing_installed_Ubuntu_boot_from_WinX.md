---
title: "[SOLVED] Repairing installed Ubuntu boot from WinXP"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by ksbalaji on 2007-08-08
Hi Ubuntu users,

I have WindowsXP-SP2 installed  in c: drive (FAT32) and also I am using D: drive (NTFS) for storing data.

Using free space  in my 80GB hard disk, I recently  installed Ubuntu from a LiveCD and after some errors somehow succeeded connecting  my LG-modem in Linux environment. GRUB was controlling the boot process excellently and dual booting was simply fun.

Then something went wrong and I had to reinstall WindowsXP.  I presume that this process has changed the  MBR and now my precious Ubuntu is no more accessible. I understand that I can rescue Ubuntu by altering boot.ini in c: drive. But how?  What text should I include to let WindowsXP chain boot? 

Please help.

---

### Post by bapoumba on 2007-08-08
Thread moved to the "Absolute Beginner Talk" support forum.

---

### Post by ron999 on 2007-08-08
It's probably best (imho) to repair GRUB with the Ubuntu LiveCD using the instructions from this thread (it worked for me). Here:-[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by ksbalaji on 2007-08-25
> **ron999 said:**
> It's probably best (imho) to repair GRUB with the Ubuntu LiveCD using the instructions from this thread (it worked for me). Here:-[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Hi Ron999 ! Thanks ! That was a great help for a beginner like me. I also seek help to chain boot from my Windows XP - something like a code to add to the existing MBR. Since I had problems with my net connection, I could not reply earlier.  Sorry for the delay.  Thanks again.

---

