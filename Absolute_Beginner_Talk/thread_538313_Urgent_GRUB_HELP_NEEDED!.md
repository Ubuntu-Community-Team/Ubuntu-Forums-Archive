---
title: "Urgent GRUB HELP NEEDED!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Noobuntu61 on 2007-08-29
Hey guys i have a large problem i think. My brother accidently deleted my linux partitions in windows. Now when i boot up my laptop the GRUB loader pops up and the system says error with no response. I am not able to enter into the boot menu with F8 on my hp laptop. Is there any way to get back the windows loader. Please i am desperate to get my pc up and running. 

Thanks for all the help guys.

---

### Post by diatribe on 2007-08-29
you could either reinstall ubuntu which will reinstall grub, or you could use a windows restore disk

---

### Post by Noobuntu61 on 2007-08-29
ok thanks once i boot from a recovery disk what must i do i don't want to completely reinstall windows.

---

### Post by w1z4rd on 2007-08-29
Boot off the windows cd into recovery mode, and type FIXMBR

---

### Post by eldara5 on 2007-08-29
I have ahd this problem and i wouldnt segest the above they all gave me 'The Blue Screen of Death'  sguuest trying to find a Super GRUB Disk, it has an option to restore the windows boot. and your cmputer will act as tho Ubuntu was never installed and will go straight to windows

---

### Post by crjackson on 2007-08-29
> **w1z4rd said:**
> Boot off the windows cd into recovery mode, and type FIXMBR

This is exactly correct.  Boot from the windows install CD.  Select recovery console. From the command line (DOS SCREEN) prompt type: FIXMBR <enter>.

Remove the CD and reboot into windows.  The Grub loader (Linux MBR) will be replaced with the windows loader (Windows MBR).

---

