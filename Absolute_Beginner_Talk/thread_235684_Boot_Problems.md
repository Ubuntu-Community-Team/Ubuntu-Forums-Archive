---
title: "Boot Problems"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Pro_photoguy on 2006-08-13
](*,) My problem is a little unique. I installed two SATA drives on a DFI motherboard. The first few times that I tried to install Ubuntu it didn't work. I ordered a new SATA controller card that supports Linux to try to fix the problem. I got all the way through the installation, but when I try to boot Linux it stops booting when it reads Grub 1.5. I can disconnect my hard drive from the SATA controller card and plug directlty into the motherboard and boot off of Windows, but When it is hooked to the SATA controller card the boot just stalls. What can I do to fix it? I don't need Linux, I'm just tired of Windows.

---

### Post by foolsh on 2006-08-13
i had a similar problem lookin your bios and see if there is compatibilty mode for your sata controller
i had too eventually boot from a IDE drive and load ubuntu from the sata drive

---

### Post by Pro_photoguy on 2006-08-16
> **foolsh said:**
> i had a similar problem lookin your bios and see if there is compatibilty mode for your sata controller
i had too eventually boot from a IDE drive and load ubuntu from the sata drive
Can you tell me what to look for in the bios? Which of the categories in the bios do I look under and what do I have to set to make it recognize the SATA controller? :D ](*,) ](*,) ](*,) ](*,)

---

### Post by foolsh on 2006-08-16
well different mother boards have different bioses but here is the information you requested

catagory "drives"
     sub-catagory "sata options"
          options
                 normal-configured for normal operation has highest             
                        performance with the most flexibility

          compatibility-configured for compatibility for older 
                        operating systems that do not support sata

if I remember right windows would boot in normal mode but not compatibility
and ubuntu would boot in compatibilty mode but not normal mode
so like I said my ide drive holds the boot sector and my sata drive has the operating systems
BTW it is set to normal mode for performance since im not booting from it
:)

---

