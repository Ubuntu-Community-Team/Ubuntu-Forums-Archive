---
title: "Dual Boot Issue"
date: 2013-10-07
forum: Any Other OS
---

### Post by Burns_Good on 2013-10-07
I have installed Ubuntu 12.04 on a new HP with Windows 8 preinstalled. Everything works fine except I NEED to have my LiveUSB connected in order to boot into Ubuntu. Any help on a solution is appreciated.

---

### Post by oldfred on 2013-10-07
Need to see details. With LiveUSB plugged in run this report. Also what model HP?
With Windows 8 you have UEFI, but did you install Ubuntu in UEFI mode or BIOS mode?

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

### Post by Burns_Good on 2013-10-08
I realized after getting some sleep that I needed to provide much more information.

Computer Model: HP 500-054
Secure Boot set to off
Windows 8 and Ubuntu 12.04 both installed in UEFI mode
Windows 8 is the "default" OS (have to keep the young lady happy)
Windows 8 starts with no problems
Ubuntu hangs on purple screen when starting and will not go any further, but will start up no problem provided I have my LiveUSB connected.
BootInfo is [http://paste.ubuntu.com/6208915](http://paste.ubuntu.com/6208915)

Also, after loading Ubuntu I CAN remove USB and continue running with no problems.
Any further help is appreciated.

---

### Post by oldfred on 2013-10-08
Not even sure which way you are booting. You have a bios_grub partition and grub in MBR which is a BIOS boot and you have grub in efi partition which is UEFI boot. As far as I know you cannot have both so which ever repair you ran last it the way you boot. It looks like you are in UEFI mode.
Boot-Repair converts a BIOS boot to UEFI if you boot Boot-Repair in UEFI mode. It can also convert a UEFI install to BIOS if required (rarely). Since Windows is UEFI you need Ubuntu in UEFI boot mode to easily dual boot.

You should be able boot boot Ubuntu from UEFI menu without flash drive, it should be ubuntu in UEFI menu. But usually video issues are black screen. BIOS boot of flash drive has a purple screen.

What video card/chip do you have?
Live install uses the very lowest level video, but install tries to run better video. With both AMD & nVidia proprietary drivers work a lot better. You often need nomodeset in grub boot stanza to get it to boot in low res mode.
If you get grub menu in UEFI mode, press e for edit, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

### Post by Burns_Good on 2013-10-09
Video card: AMD Radeon HD 7560D

Currently trying a few things that you mentioned (and hoping for something to solve my issue).

---

### Post by oldfred on 2013-10-09
I do not know the details of AMD as I have nVidia. 
Some links on AMD video:

       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[URL="http://ubuntuforums.org/showthread.php?t=2050320"]http://ubuntuforums.org/showthread.php?t=2050320
[/URL]
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

[URL="http://ubuntuforums.org/showthread.php?t=2050320"]
[/URL]

---

### Post by Burns_Good on 2013-10-12
So as of now, after trying everything that was suggested (along with some hairbrained ideas I had along the way) I am still where I was. I can load Ubuntu, but ONLY with LiveUSB connected. Oddly enough, this does not send me into a Live session, but instead gives me full access my Ubuntu partition. Also, provided I do not enter Windows 8, I can continue to load into Ubuntu as often as I please WITHOUT the LiveUSB. As soon as I go to Windows 8, forget about it, re-insert USB and do it again.

So my question, as it stands now, is what else can I do? Or would a different distribution work better? As I said before (as much as I'd love to ditch Windows), I need to keep it around.

---

### Post by oldfred on 2013-10-13
Do you have secure boot on?

I think one user posted that Windows automatically turned secure boot or reset to directly boot Windows whenever he booted into Windows. If secure boot is on, only secure boot systems will boot. So maybe you have one of the few systems that has to have Ubuntu installed in secure boot mode to be compatible. Or you need to change some settings in UEFI/BIOS.

---

### Post by Burns_Good on 2013-12-31
I think I have this one solved, in a fashion. I still have to jump through some hoops, but I can access everything.

After resetting my PC to factory settings (to ensure I got rid of everything and had an original Windows 8 running), I ran through all of my Windows updates and created a new partition on my hard drive from within Windows. Being that I was having no luck with Ubuntu 12.04 working in my particular case, I decided to try 13.10. I turned off Fast Restart, but left Secure Boot on.

I currently have a Windows 8.1/Ubuntu 13.10 dual boot with only the side effect that to load Ubuntu I need to restart my PC and go though the Startup menu and manually sellect Shimx64.efi
The reason for this (and I have tried fixing it a few times through various avenues) is that Windows keeps changing the Bootx64.efi file back to the way it wants it (and also a loads that instead of Grub) and in the process my Grub menu is ignored until I manually sellect it.

Not the ideal way to start a dual boot, I admit, but it IS working.

---

### Post by oldfred on 2013-12-31
I have seen this as a fix for Windows resetting. Windows does try to mirror the UEFI NVRAM in its BCD. So change BCD to include shim or grub. I think you would need shim if secure booting.
 Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by Burns_Good on 2014-01-02
I've tried changing BCD both from within Ubuntu and from Windows, but Windows keeps changing it back every time I exit from Windows. Until such time as I get a more permanent fix, I will continue to load Ubuntu as I need. At least it works now. Thanks for all of your help and advice oldfred.

---

