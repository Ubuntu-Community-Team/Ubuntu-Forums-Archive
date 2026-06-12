---
title: "Trying ubuntu from USB on 8 doesn't work"
date: 2013-04-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Waaayoff on 2013-04-28
I have ubuntu on USB and i successfully booted it on my windows 7 desktop. However it doesn't work on my asus laptop which has windows 8. I disabled fast run in the bios menu then choose to boot from USB. After that i get a dark screen and windows 8 starts normally...

I don't know if this is relevant but the bios is in text and not that UEFI thingy

---

### Post by oldfred on 2013-04-28
Did you follow these instructions?
 You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Post link:

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Waaayoff on 2013-04-30
Ok so i downloaded the 12.04 64bit version and when i reboot from usb, i get to select Try Ubuntu Without Installing, but then i just get a blank screen...

---

### Post by oldfred on 2013-04-30
What video card/chip?

Often nomodeset required.
With UEFI boot you get a grub menu more like you do when booting normally, See later screens showing first boot after install. You have to use e on grub menu and on linux line replace quiet splash with nomodeset. Sometimes other boot parameters are required.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

