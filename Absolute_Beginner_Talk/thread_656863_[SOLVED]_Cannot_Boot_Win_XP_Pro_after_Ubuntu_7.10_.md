---
title: "[SOLVED] Cannot Boot Win XP Pro after Ubuntu 7.10 Install"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by NuUb710 on 2008-01-03
Greetings, 

Sometime ago I installed Ubuntu 7.10 on an USB flash drive attached to the 
laptop (a few months old AMD based Dell Inspiron 1501), then I lost the USB 
drive. 
When I tried to boot without the USB drive I was getting a GRUB Error 21 or 
26. 
I then read some postings about removing the GRUB, but it did not work (the 
GRUB Error has been replaced with "Operating System Not Found"). 
Since then (about 3 weeks ago) I have been reading all the message boards 
and tried pretty much everything, except re-installing Windows which I am 
trying to avoid if possible. Here is a list of what I tried (some multiple 
times) without any success so far: 

- FixMbr from RECOVERY CONSOLE 
- FixBoot from RECOVERY CONSOLE 
- Bootcfg /Rebuild (it comes back with Error, I tried Chkdsk /p which says 
the disk is OK) from RECOVERY CONSOLE 
- Ran REPAIR from Windows XP setup CD ("R" option when going into SETUP, not 
into RECOVERY CONSOLE). The repair detects the C:\Windows installation and is 
asking if I want to REPAIR it (yes). 

I have another USB stick I made with a reduced version of Windows XP and I 
can boot from it order to access the HD, so I know the HD is detected by the 
BIOS and working. 

I appreciate any suggestions or ideas...thanks!

---

### Post by kcy29581 on 2008-01-03
Could you elaborate on what OSs are installed on your hard drive, how many hard drives you have, which one is the "first" one in the BIOS, etc?

Just a bit confused as to what you are trying to boot on the PC without having a USB flash drive attached.

---

### Post by ubutufan on 2008-01-03
I am confused with your configuration.
If your MBR (the one of Windows) is still there, then your partition of windows might not be active. If so, then use Gparted and mark the windows partition as active. That will enable the windows MBR to boot windows.
Otherwise explain details so we can give suggestions

---

### Post by r4ik on 2008-01-03
Perhaps Super Grub Disk can help,

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Good luck !

---

### Post by NuUb710 on 2008-01-03
> **kcy29581 said:**
> Could you elaborate on what OSs are installed on your hard drive, how many hard drives you have, which one is the "first" one in the BIOS, etc?

Just a bit confused as to what you are trying to boot on the PC without having a USB flash drive attached.

I have a single hard disk that has Windows XP Pro in the default directory C:\Windows (it came factory configured from DELL).

The BIOS is configured to boot from USB, then CD then C:\ and it appears to be working (if I remove the USB stick with Win XP it boots from the CD and if there is no CD it seems to look for the hard drive and it comes back with the "Operating System Not Found".

I tried moving the hard drive in the BIOS at the first position and I get the same "Operating System Not Found" regardless if the USB stick (with the bootable Win XP) or Win XP install CD are present.

Thanks!

---

### Post by NuUb710 on 2008-01-03
> **kcy29581 said:**
> Could you elaborate on what OSs are installed on your hard drive, how many hard drives you have, which one is the "first" one in the BIOS, etc?

Just a bit confused as to what you are trying to boot on the PC without having a USB flash drive attached.

I have a single hard disk that has Windows XP Pro in the default directory C:\Windows (it came factory configured from DELL).

The BIOS is configured to boot from USB, then CD then C:\ and it appears to be working (if I remove the USB stick with Win XP it boots from the CD and if there is no CD it seems to look for the hard drive and it comes back with the "Operating System Not Found".

I tried moving the hard drive in the BIOS at the first position and I get the same "Operating System Not Found" regardless if the USB stick (with the bootable Win XP) or Win XP install CD are present.

Thanks!

---

### Post by NuUb710 on 2008-01-03
> **ubutufan said:**
> I am confused with your configuration.
If your MBR (the one of Windows) is still there, then your partition of windows might not be active. If so, then use Gparted and mark the windows partition as active. That will enable the windows MBR to boot windows.
Otherwise explain details so we can give suggestions

Thanks a lot ubuntufan!

I used the LiveCD version of "Gparted" to set the flag on the Win XP partition as bootable.
After that I was able to boot into Win XP (it went through a "Repair" installation using the CD, but I ended up with the same original configuration without having to re-install the other applications).

Thanks again!

---

### Post by NuUb710 on 2008-01-03
SOLVED  Re: Cannot Boot Win XP Pro after Ubuntu 7.10 Install

---

### Post by ubutufan on 2008-01-04
Very pleased you have your system up and running

---

