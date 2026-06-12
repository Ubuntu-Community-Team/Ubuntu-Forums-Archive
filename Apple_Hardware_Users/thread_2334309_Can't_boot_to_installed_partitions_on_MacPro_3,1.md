---
title: "Can't boot to installed partitions on MacPro 3,1"
date: 2016-08-18
forum: Apple Hardware Users
---

### Post by mike-g2 on 2016-08-18
I've been unable to boot to my main hard drive successfully since upgrading from Ubuntu 14.04.4 to 16.04.1.
[LIST=1]
[*] I apparently had a 'legacy bios' set up before the upgrade.
[*] I have a number of different installations of linux on the machine
[*] I don't have OSX or Window installed.
[*] Post-upgrade I have installed rEFInd  in hopes of fixing the problem.
[*] I ran boot-repair via a live CD.  The output can be found at [http://paste2.org/6Uc778Gx](http://paste2.org/6Uc778Gx)
[*] When the computer is started, I get a grub2 menu which, depending which option I choose, takes me to a rEFInd screen.
[*] I have numerous options in rEFInd, but the only ones that work are for the 16.04.1 Live CD 
[/LIST]

I'd appreciate some help solving this problem and getting my computer back up and running.

---

### Post by oldfred on 2016-08-18
I do not know Mac.

But  you are showing two ESP - efi system partitions. While UEFI spec may allow 2, most systems will not work with more than one per device/drive.

```
 Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                    40       409,639       409,600 EFI System partition
/dev/sda2               409,640     1,464,319     1,054,680 EFI System partition 


```

Your sda2 looks like a /boot partition so remove UEFI boot flag from it.

You may have hybrid partitioning since you show 4 MBR partitions. That really was only a requirement for older Windows that would only boot in BIOS mode from a primary MBR partition. Ubuntu boots either UEFI or BIOS from gpt as long as you have either the ESP or bios_grub.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html) 
    
And you have installed grub to the partition boot sectors of several partitions. That should not normally be done. Grub is installed to a drive like sda for both BIOS or UEFI boot. With UEFI, grub knows to put efi boot files in the (one) ESP on drive seen as sda.

---

### Post by mike-g2 on 2016-08-21
Thanks for the input, removing the esp flag was key.  More generally, it helped me understand the problem and, in turn, solve it. (or at least appear to solve it).  I now get a grub screen on boot.
  
Some key insights were also 

[LIST=1]
[*] Being able to access and control the boot loading before grub by holding alt during start up.
[*] Removing spurious msftdata flags on partitions.
[/LIST]

It seems to be working but I'd like to figure out if it's okay to remove some or all of the efi boot options from grub listed below.
[LIST]
[*]  /Boot/bootx64.efi /ubuntu/shimx64.efi 
[*]                       /EFI/BOOT/bkpbootx64.efi /EFI/BOOT/bootx64.efi 
[*]                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
 [*]                      /EFI/ubuntu/shimx64.efi /Microsoft/Boot/bootmgfw.efi 
   [*]                    /Microsoft/Boot/bootx64.efi 
    [*]                   /EFI/Microsoft/Boot/bootmgfw.efi 
[*]/EFI/Microsoft/Boot/bootx64.efi
[/LIST]
 
THanks again for your input.

---

### Post by oldfred on 2016-08-21
Do not know with Mac what is required or not.

/EFI/Boot/Bootx64.efi is the fallback or hard drive boot entry. Windows systems often make that file be a copy of Windows boot .efi file. But Boot-Repair copies shimx64.efi to be that file as a second (some poorly designed UEFI, the only) way to boot.

the bkpbootx64.efi was created by Boot-Repair.
MoKManager.efi is for creating and using your own keys. I am not sure that Mac even supports Secure boot?

You seem to have copies of files in non-standard locations. 
I would suggest a full backup of the entire ESP or efi system partion. It should not be large, although Boot-Repair may have saved other log files into it.

 Typical files & folders from Boot scripts for PC, Mac may have others:
Boot files:        
/efi/Boot/bootx64.efi 
/efi/ubuntu/grubx64.efi
/efi/ubuntu/shimx64.efi
/EFI/Microsoft/Boot/
/EFI/refind/refind_x64.efi

---

