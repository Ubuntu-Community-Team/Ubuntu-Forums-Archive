---
title: "Issues with triple boot install"
date: 2016-06-09
forum: Apple Hardware Users
---

### Post by elliot.campbell on 2016-06-09
Hi,

I am trying to install Ubuntu on an iMac running Windows 7 in Bootcamp along with OS X. I believe I have Ubuntu installed, but received an error at the end that it couldn't install the boot loader. I have tried the repair utility in the Mac OS recovery as well as the boot-repair-disk live distro. 

I am still getting an error that no bootable devices are found. 

Log here:
[http://paste.ubuntu.com/17137491/](http://paste.ubuntu.com/17137491/)

Please let me know if you have any ideas.

Thanks in advance!

---

### Post by QIII on 2016-06-09
*Moved to **Apple Hardware Users** for better response.*

---

### Post by oldfred on 2016-06-09
I do not know Mac, but have seen some of the issues.

Older Mac & older Windows used BIOS/MBR even though a Mac is UEFI with gpt partitioning.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
With hybrid partitioning you have both MBR & gpt, and must keep the first 4 partitions in sync. Windows only installs in BIOS mode to one of the first 4 MBR partitions.
Do not know if Windows 7 in UEFI mode will work.
 

 [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios)

I think all new info suggests using UEFI.

 Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210) 

[URL="http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios"]
[/URL]

---

### Post by elliot.campbell on 2016-06-09
Thanks for the info. I believe Windows 7 was booting in UEFI mode through Bootcamp. At least I could see it as the Bootcamp partition in the UEFI launcher. 

My plan now is to try installing rEFIt ([http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)) on the Mac partition, and setting boot options through there (per this support doc: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) ). 

I will report back how it goes. Please let me know if anyone has experience with rEFIt or any pitfalls to watch out for.

---

### Post by oldfred on 2016-06-09
I though refit was not supported anymore, and rEFInd was updated fork.
       [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by elliot.campbell on 2016-06-09
Thanks for the link! I will try rEFInd. 

Maybe this link should be updated: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by elliot.campbell on 2016-06-09
rEFInd worked to solve the bootloader issue, but I received an error when starting Ubuntu. Something about not finding the /root mount point, or it being on the current file system? I figure something went wrong with the partitioning, so I will try installing Ubuntu to the partition I made again.

---

### Post by elliot.campbell on 2016-06-10
Reinstalled Ubuntu, reinstalled rEFInd, triple boot setup appears to be working properly.

Thanks for the help!

---

