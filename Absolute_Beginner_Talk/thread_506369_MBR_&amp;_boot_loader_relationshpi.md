---
title: "MBR &amp; boot loader relationshpi"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2007-07-21
A theoretical question: What is the relation ship between the MBR and boot loader on Linux and/or Windows systems? Are both required? Where do they reside on the hard drive? 

My understanding is that each hard drive has one MBR which determines which partition to boot from. The boot loader comes immediately next which transfers low levels programs from the hard drive to the RAM.

---

### Post by ddrichardson on 2007-07-21
Your understanding is correct.

MBR is physically at the start of the disk, and is handed over to by BIOS. NTLDR handles Windows booting via the boot.ini file, Linux uses Grub or LILO.

---

### Post by artir on 2007-07-21
The bootloader lives on the MBR of the boot devide, usually /dev/hda or /dev/sda. In ubuntu systems, GRUB is the bootloader. The bootloader itself is installed on the MBR, but his configuration files are on the ubuntu folder /boot/grub i think.
Then when you choose a SO, our friend GRUB launches that SO and gives the control of the PC to that SO.

---

### Post by ddrichardson on 2007-07-21
> **artir said:**
> The bootloader lives on the MBR of the boot devide, usually /dev/hda or /dev/sda. In ubuntu systems, GRUB is the bootloader. The bootloader itself is installed on the MBR, but his configuration files are on the ubuntu folder /boot/grub i think.
Then when you choose a SO, our friend GRUB launches that SO and gives the control of the PC to that SO.

This isn't entirely correct - the first stage boot loader is in effect BIOS as there is nothing to tell the processor what to do at switch on other than what comes from CMOS - i.e a bootstrap loader. After self test a bootable device is saught.

This ofcourse hands over to the second stage boot loader - in this case Grub. The selections from the second stage bootloader in a multi-os setup then loads whatever boot loader resides on the selected partition.

Grub installed on the MBR in the case of multi-boot systems is the norm that much is true but only really by convention because what it actually does it check the partition table for a bootable flag.

Sorry - I'm being very nit-picky. ;-)

---

### Post by dfreer on 2007-07-21
> **ddrichardson said:**
> Your understanding is correct.

MBR is physically at the start of the disk, and is handed over to by BIOS. NTLDR handles Windows booting via the boot.ini file, Linux uses Grub or LILO.

This is pretty much it. The MBR is like the first 512 bytes on an hard drive. You need both the MBR and a boot loader to load an OS, although which one you use is a matter of preference. Note that if you use a linux based bootloader, and tell it to boot windows, it will still load NTLDR cuz that is the way it works. Same thing if you use NTLDR to boot GRUB/LILO/whatever.
NTLDR is located at C:\ntldr and it's entries are controlled with C:\boot.ini.

---

### Post by Ephilei on 2007-07-21
So when dual booting Windows and Linux (say, Ubuntu) I should overwrite the WIndows bootloader with Grub? I know the Windows bootloader can choose between Window OSes; can it choose between non-Win OSes?

---

### Post by ddrichardson on 2007-07-21
It can but not very well and its a pain in the backside to configure. Not to mention its broken if you need to re-install Windows. Grub on the MBR is the easiest solution.

---

### Post by dfreer on 2007-07-21
> **ddrichardson said:**
> It can but not very well and its a pain in the backside to configure. Not to mention its broken if you need to re-install Windows. Grub on the MBR is the easiest solution.

Agreed. It is eaiser to use GRUB in terms of setup. However, it can be eaiser if you plan on wiping Ubuntu and going back to windows only to use NTLDR, because all you would need to do is clear the entry in C:\boot.ini instead of having to FIXMBR. All NTLDR can do is load GRUB, it can't load a linux kernel directly, but the same is true about GRUB booting windows, it still only boots the NTLDR.

EDIT: Note also, you aren't overwriting windows bootloader, just the MBR. it's a semantical difference but important just the same. The MBR basically just points to the bootloader to use, either NTLDR or GRUB

---

