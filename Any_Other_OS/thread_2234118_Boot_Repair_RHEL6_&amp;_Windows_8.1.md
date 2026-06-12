---
title: "Boot Repair: RHEL6 &amp; Windows 8.1"
date: 2014-07-12
forum: Any Other OS
---

### Post by lbalbalba on 2014-07-12
Hi,


Im running into some boot loader issues, and was hoping boot repair could help me. Im not running Ubuntu but the BootRepair web site directed me here, so I hope you can help me.

Im trying to dual boot Red Hat Enterprise Linux 6.2 and Windows 8.1. When I select my SSD that windows is installed on in my UEFI/BIOS as device to boot from, Windows boots normally. If I let grub boot Red hat, red hat boots normally. But I cant seem to get Windows to boot without having to enter my UEFI/BIOS. When I choose the Windows entry in grub that the red hat installation created, the system just seems to freeze.

I let boot rescue create a paste bin entry here:
[http://pastebin.ubuntu.com/7784496](http://pastebin.ubuntu.com/7784496)


Regards,


John Smith.

---

### Post by howefield on 2014-07-12
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by oldfred on 2014-07-13
You have to boot the way you are.
UEFI and BIOS are not compatible and once you start booting in one mode you cannot change. Or grub only boots systems installed in the same boot mode.

You have Redhat in UEFI boot mode and Windows in BIOS boot mode.

Windows only boots from MBR(msdos) drives with BIOS.
Windows only boots from gpt partitioned drives with UEFI.
I know Ubuntu will boot from gpt with either BIOS or UEFI and I think that is just grub2 is different, so I would expect Redhat to also work.

---

### Post by lbalbalba on 2014-07-13
> **oldfred said:**
> You have Redhat in UEFI boot mode and Windows in BIOS boot mode.
Ah. I thought I had Windows in UEFI mode, so I chose to instal Red hat in UEFI mode as well. So would re-installing Red Hat in BIOS mode solve my issue, then ?

*EDIT*

Hrm. I thought I could install RHEL6 in BIOS mode by booting from DVD-DRIVE instead of UEFI_DVD_DRIVE in my UEFI firmware. That didnt work, it still installs RedHat in UEFI mode.

---

### Post by oldfred on 2014-07-13
Perhaps Redhat is smarter and once it sees gpt partitioned drive it installs with UEFI. 
Or it may have another way to select? With Ubuntu it always is how you boot installer.
Redhat's default install is the LVM which I know less about.

With Ubuntu Boot-Repair converts a UEFI install to BIOS if you create a bios_grub partition first 1 or 2MB unformatted with bios_grub flag. It uninstalls the version fo grub that is UEFI with Ubuntu grub-efi or now I think it is grub-amd64-efi-signed? and then installs grub-pc. You can manually do that but make sure Internet is working as without any grub you would not be able to boot.

---

### Post by lbalbalba on 2014-07-13
Well I created a unformatted partition and labelled it bios_grub with GParted. But when I ran Boot Rescue, it complained that it couldnt locate a source repository for grub2. So I removed all partitions (boot, red hat lvm, bios_grub) and reinstalled Red hat on that drive. Im not sure that happened exactly, but my system now only boots in Windows 8 and refuses to boot from the freshly installed red hat drive. 

So I guess Ill have to boot from some sort of rescue disk, maybe even BootRepair, get a root prompt, mount the lvm and /boot filesystems, and manually install grub2 ? I dont see any other options here, any ideas on what else to do or how to do the manual grub2 install ? Thanks for the help so far, by the way.

---

### Post by oldfred on 2014-07-13
Do not know many details of Redhat. (my last install was Redhat 7.1 from about 2001) :)
Did you specify to install grub to the Linux drive. And then in BIOS change to boot that drive in BIOS/CSM/Legacy mode? If booting Windows you must be booting Windows drive in BIOS.

Boot-Repair may work as it will also mount LVM, but you may have to use the chroot or full uninstall reinstall option, so it installs your correct version. And you want it installed to the MBR of the Linux drive. And if gpt you still need bios_grub. 

Not sure how manual install of grub-pc (if that is your version for BIOS) is different than Ubuntu's.

I used XP on a MBR drive and Ubuntu on a gpt drive with BIOS since about Ubuntu 10.10 or Oct 2010.

---

### Post by lbalbalba on 2014-07-15
Hrm. The drive im installing Linux on is 4TB, so I it looks like im stuck with GPT/UEFIfor that disk. Apparently the RHEL6 install figures that out on its own, and automagically chooses GPT/UEFI instead of BIOS/MBR. 

So the only remaining option could be to convert the MBR disk on which Windows is installed to GPT/UEFI ? The 'C:' drive already has an '/EFI' directory, with (the required ?) files. I tried to convert the disk using Windows Disk Manager, but there the option is greyed out/unavailable. This tool claims it can do the conversion as well: [http://gptgen.sourceforge.net/](http://gptgen.sourceforge.net/) ?

---

### Post by oldfred on 2014-07-15
Ubuntu will boot from gpt drives with BIOS and I think that is all grub so Redhat should also.
If drive is blank, I know the Ubuntu installer automatically uses gpt if drive is somewhere over 1.5TB. But gpt is only required if drive is over 2TiB.
If in BIOS boot mode you need a bios_grub partition. If in UEFI mode you need an efi partition and it should be near beginning of drive.

Windows only boots from gpt partitioned drives with UEFI.

Both Linux & Windows only boot from MBR(msdos) partitioned drives with BIOS/CSM/Legacy boot modes.

---

