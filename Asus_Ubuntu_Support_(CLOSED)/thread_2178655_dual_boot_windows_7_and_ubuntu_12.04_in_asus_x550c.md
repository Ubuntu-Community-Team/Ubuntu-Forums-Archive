---
title: "dual boot windows 7 and ubuntu 12.04 in asus x550cc"
date: 2013-10-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pay3 on 2013-10-04
Hi guys,
pls help me I am using ASUS X550cc which which has gpart hdd and  uefi.
first i tried to install windows 7 and then ubuntu 12.04.
but while installing ubuntu 12.04 it did not  showed windows 7.
and after installing ubuntu my laptop directly starts booting from ubuntu without asking for windows 7.
pls reply ASAP.

---

### Post by oldfred on 2013-10-04
Even if your system is UEFI, it has a BIOS/CSM/Legacy boot mode. If you installed Windows 7 from DVD without converting to flash and adding UEFI features, it will just install in BIOS mode. 
But when Windows installs in BIOS mode on a drive that was gpt, it incorrectly removes the gpt partitioning. It leaves the backup partition table. Then Linux sees MBR partitions and backup gpt and is not sure what you really have.

If you know your are in BIOS mode.
 
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If unsure best to see details.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by pay3 on 2013-10-04
can u give precise information about how to dual booting from starting i want to format my hdd.(i want to dual boot windows 7 and ubuntu 12.04).
here are my laptop config-
model name =ASUS X550cc
hdd gpt with uefi
what softwares will be required for dual booting

---

### Post by oldfred on 2013-10-05
Do not know about Windows 7. Last Windows I installed was XP 7 years ago.

Lots of links in the link in my signature. First two show screen shots of installing. 
Do you want BIOS or UEFI? Big difference on how you install.
Boot-Repair can convert an Ubuntu install if in wrong mode.

       Product key now in UEFI/BIOS for Windows 8.
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

 Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
 [http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

