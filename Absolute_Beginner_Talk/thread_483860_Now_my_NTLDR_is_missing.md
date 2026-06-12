---
title: "Now my NTLDR is missing"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2007-06-25
I changed some option in Kubuntu that didn't let Kubuntu load so I reinstalled it again.  In the process I made Windows and Kubuntu unbootable.  Since I have a second hard disk, I installed kubuntu in the second hard disk.  Now the Kubuntu installation in the main hard disk works but not Windows (Its says that NTLDR is missing).  If I change to the second hard disk and select Windows from the available OS, it loads without trouble.  I checked in the Grub folder the menu.lst and is basically identical in both Kubuntu installations (the disks ID are different, but I believe that is normal behavior).  Any help?

---

### Post by KIAaze on 2007-06-25
I am not sure, but maybe this thread could help:
[http://ubuntuforums.org/showthread.php?t=450329]("http://ubuntuforums.org/showthread.php?t=450329")

There seems to be a solution top the NTLDR problem at the end. ;)

---

### Post by notbitmonk on 2007-06-25
It appears that the problem described in the referred post is related to a corrupt boot.ini file.  If I tell grub to load Windows when I boot from my second hard disk, Windows loads without problems.  I'll check if there is a boot.ini file on my second hard disk and compare it from the boot.ini from the first hard disk.  Any other thoughts?

---

