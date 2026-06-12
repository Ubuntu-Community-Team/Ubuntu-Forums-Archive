---
title: "Mac Grub"
date: 2013-01-09
forum: Apple Hardware Users
---

### Post by Cpierce on 2013-01-09
I have a triple boot computer with Mac, Ubuntu 12.04, and win7. Ubuntu is installed on sda3. I had installed grub inside sda3 as not to screw up the mac boot loader that I need. 

I use grub customizer to remove the old kernels from showing up on the startup screen and change backgrounds. The old grub customizer allowed you to just uncheck the boxes to hide the old kernels. The new version I have to "delete" the kernel option to keep them from showing up. Well after an update it added a new kernel so I went into grub customizer to delete the old one. I saw I had two entries for the same kernel, so I deleted one of them. When I rebooted I have an error message and the "Grub>" prompt. 

When I have grub problems on a dual boot system, and grub is the primary bootloader for the entire drive, I boot up on the ubuntu liveCD, open terminal and run:
                     
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX

I did this; selecting sda3 in the first line, and instead of selecting sda in the second line, I did sda3 here as well. It didn't work. 

I am scared to select sda for the second line because I am worried grub will install over the primary GPT bootloader I need for Mac

What should I do ? Please help

---

### Post by Cpierce on 2013-01-10
Update:

I read where to force grub to install on a certain partition and tried this:

booted up on liveCD
opened terminal and ran
       sudo mount /dev/sda3 /mnt
       sudo grub-install --root-directory=/mnt --force /dev/sda3

Said it installed successfully with no errors, but when I try to boot up I still get the grub> prompt.

Any help would be greatly appreciated.

---

### Post by oldfred on 2013-01-10
I do not know Macs.

Moved you to the Apple sub-forum where those who know more may help.

---

### Post by Cpierce on 2013-01-10
Thank you. I don't think it is an Apple issue, but it won't hurt to ask them. I just need to re-install grub and keep it inside my Ubuntu partition. Of the three OS's, I use Ubuntu 99% of the time so I am really missing it.

---

### Post by Cpierce on 2013-01-10
read another command that had worked for other people running 12.04. so I tried 

sudo mount /dev/sda3 /mnt
sudo grub-install --boot-directory=/mnt/boot/ --force /dev/sda3

again it said it installed correctly, but when I try to boot to my ubuntu I still get the grub> prompt.

I can still boot to mac and win7 with no issues.

---

### Post by oldfred on 2013-01-10
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

If you are in BIOS mode to boot Ubuntu you need a bios_grub partition for grub to install correctly. It needs that on all gpt drives unless you boot Ubuntu with UEFI.

       In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. 

BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

    
I do not know if Boot-Repair fully works on Mac or not.But create bios_grub first.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

       Alternative efi boot loader for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
       Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards]("https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards")

---

### Post by Cpierce on 2013-01-10
Thank you Oldfred ! I don't know if I understand all this, but I sure will dive in. Looks like I have some homework to do. 

Again......Thank you

---

### Post by danielrichter on 2013-01-11
For me it looks like an error in your grub.cfg. This cannot be solved by running grub-install as you have to create a new config. This is the job of update-grub.

Before you do the following, please create a backup of your /boot/grub/grub.cfg - if there's an issue i'd like to see this file afterwards.

You can use grub customizer from a live cd. Just install it as usual. When you run it, you should be inside the environment setup which lets you choose the root partition of your system. Then you can load your config. Use the "revert" button to restore the default boot options. Then save it and reboot.

---

### Post by Cpierce on 2013-01-11
Daniel, 

Thank you so much. I will try this as soon as I get back to my laptop. This makes a lot of sense and looks like it is going to work.

Thank you

---

### Post by Cpierce on 2013-01-11
Daniel,
That worked like a charm. I am ever so grateful. Thank you very much, I learned something today.

You truly are the grub master !

---

