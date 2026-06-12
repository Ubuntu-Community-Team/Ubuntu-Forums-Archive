---
title: "[SOLVED] Deleted Ubuntu partition from Vista, now GRUB 22 error"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by T3KN33K on 2007-10-01
....the catch is, i no longer have the vista installation disk...  I've tried to boot into recovery console with an XP disk, but no go.  Is there any way I can fix this with the Ubuntu live disk?   ...otherwise my only option is to DL another copy of vista, burn to dvd, and go from there, which will take WAY longer than I have ATM....

---

### Post by ugm6hr on 2007-10-01
You will have to reinstall GRUB / Ubuntu.  Did you remove the Ubuntu partition or just delete the contents?

If the latter - reinstall Ubuntu, then boot into Vista and install EasyBCD: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

This should reinstall the Vista bootloader.

If you actually removed the partition and resized, you might have to reverse that process....

---

### Post by T3KN33K on 2007-10-01
I figured that this was a common enough issue that I need not explain indepth....  but, failing that, here's the details:

I dual boot Vista and Ubuntu Fiesty, but I recently decided to uninstall Ubuntu in favor of installing Ubuntu Studio Fiesty.  So, from the Vista disk manager, I deleteted the Ubuntu partition and left it as unpartitioned space.  So I reboot my system, and I get error message "Error 22" when Grub attempts to load. 

I have read in other posts that this is easily fixed by using the command "fixmbr" after booting into the recovery console with the Vista install disk, but, as previously mentioned, I do not have the install disk...  Is there anyway I can correct this with the live Ubuntu Cd?

**_EDIT:_** Posted prior to seeing post #2.

---

### Post by alienexplorers on 2007-10-01
Get a copy of the super grub disk.  With it repair your mbr.

---

### Post by T3KN33K on 2007-10-01
> **alienexplorers said:**
> Get a copy of the super grub disk.  With it repair your mbr.

Beautiful!  Thank you very much for the suggestion, alienexplorers, it worked like a charm!

---

### Post by moparmudder420 on 2008-03-01
is there n e way i can redirect grub to look at my vista partition, or remove grub from the ubuntu terminal, or can i use an xp recovery disk from another computer and use the dos command line to boot into vista? thanks

i accidently deleted the whole ubuntu partition a resized the drive, vista really blows but i dont want to use gparted, takes to long, i just want to get into vista once so i can make a partition

---

### Post by Aurora@FleetBuzz on 2008-03-10
You can repair Vista's bootloader very easily if you have the Vista Install disk.  Here is a link that gives you instructions.  
[http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)
> Please not that there are always risks of corrupting your data when toying with the MBR (Master Boot Record) so please back up your data before attempting this.

   1. Insert your Windows Vista Install DVD and boot from it.
   2. After selecting your language options choose the “Repair your computer” option in the bottom left corner.
   3. Select your Windows Vista Installation and continue (note: my screenshot does not show an installed OS because there is none).
   4. Open a new Command Prompt window
   5. When command prompt is open, type the following commands (note: my screenshot shows an error as vista is not installed)
         1. Bootrec /fixboot
         2. Bootrec /fixmbr

The MBR/Boot Loader’s are now repaired, restart your computer and it should boot in to Vista where you can then delete the Linux partitions from the hard drive if you wish.

---

