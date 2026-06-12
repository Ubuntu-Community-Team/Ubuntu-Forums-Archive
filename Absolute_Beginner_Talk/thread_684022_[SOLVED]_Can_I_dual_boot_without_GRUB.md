---
title: "[SOLVED] Can I dual boot without GRUB?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Dark_Jester on 2008-01-31
Hi guys, I'm trying to dual-boot XP and Gutsy Gibbon on my laptop and being a Linux noob, I'm having a few problems.

The main issue is this: I don't want to use GRUB. I have a nice partition boot manager that I've used for a few years and I'd like to use that instead. If I install Ubuntu from the LiveCD and tell it not to include GRUB from the advanced options then I can't boot the partition I put Ubuntu on, and if I let GRUB be installed it is displayed when I boot my WinXP partition rather than when I boot my Ubuntu partition. It's driving me nuts. 

If it helps, the boot manager I want to use is called "Partition Boot Manager" or PBM and the hard drive is laid out as follows: 15Gb NTFS (WinXP) - 10Gb Ext3 (Ubuntu) - 1Gb Swap - Unpartitioned space.

---

### Post by billgoldberg on 2008-01-31
> **Dark_Jester said:**
> Hi guys, I'm trying to dual-boot XP and Gutsy Gibbon on my laptop and being a Linux noob, I'm having a few problems.

The main issue is this: I don't want to use GRUB. I have a nice partition boot manager that I've used for a few years and I'd like to use that instead. If I install Ubuntu from the LiveCD and tell it not to include GRUB from the advanced options then I can't boot the partition I put Ubuntu on, and if I let GRUB be installed it is displayed when I boot my WinXP partition rather than when I boot my Ubuntu partition. It's driving me nuts. 

If it helps, the boot manager I want to use is called "Partition Boot Manager" or PBM and the hard drive is laid out as follows: 15Gb NTFS (WinXP) - 10Gb Ext3 (Ubuntu) - 1Gb Swap - Unpartitioned space.

I'm presuming you installed that boot manager from windows?

So theoricatlyj if you install ubuntu, grub will be installed. If you then would boot into windows you could set up that boot manager (it should overwrite grub).

But I'dont see why you wouldn't want to use grub.

---

### Post by Blutack on 2008-01-31
If your boot manager supports booting linux kernels then you simply make sure you go into the "Advanced Options" during the ubuntu install (on one of the pages, I forgot which!) and uncheck the Install Bootloader option.

---

### Post by Dark_Jester on 2008-01-31
> **billgoldberg said:**
> I'm presuming you installed that boot manager from windows?

So theoricatlyj if you install ubuntu, grub will be installed. If you then would boot into windows you could set up that boot manager (it should overwrite grub).

But I'dont see why you wouldn't want to use grub.

PBM is OS idependent and installs from a bootable CD. I like it because it lets you backup your partition tables and is hence immune to the fumblings of OS installers. :)

---

### Post by LowSky on 2008-01-31
> **Dark_Jester said:**
> , and if I let GRUB be installed it is displayed when I boot my WinXP partition rather than when I boot my Ubuntu partition. It's driving me nuts. 


ok this makes no sense

first off grub can be configured to boot windows or ubuntu in any order you want


but if you want to use PBM then you might have to reinstall it after you install ubuntu with out grub, I know the Alternative install CD has the option.

---

### Post by Bartender on 2008-01-31
What if he installed GRUB to the Ubuntu partition?  Don't know if that would work but at least that way GRUB wouldn't mess with the MBR.

---

### Post by Dark_Jester on 2008-01-31
I have solved it - somehow.
I was messing about and reinstalled the LiveCD, then PBM. Ubuntu now loads when I select the Linux partition in PBM with GRUB set to leave me alone and just start it, and GRUB doesn't appear when I select the Windows partition. Hurray for magic! :)

I guess this time around the LiveCD must have put GRUB in the Ubuntu partition where it belonged. No idea how to do it myself so I remain shrugged on that one. 

Thanks guys.

---

