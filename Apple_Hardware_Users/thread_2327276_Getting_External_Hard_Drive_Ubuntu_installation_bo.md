---
title: "Getting External Hard Drive Ubuntu installation bootable without rEFind"
date: 2016-06-09
forum: Apple Hardware Users
---

### Post by Turon on 2016-06-09
I have Ubuntu 14.04.2 installed to a external hard drive mainly to provide more space and because I'm a little nervous about installing directly to the internal. I've accessed this external installation mainly with rEFind on a flash disk (I couldn't install rEFind directly to the iMac) but I find that a little clunky now. I want to be able to just boot up the iMac hold down Option/Alt and select Ubuntu. Now I've tried a few things already first I followed [this]("http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf") tutorial though I got stuck when I had to type in the terminal on the live flash disk.

Ultimately I just cloned the EFI partition on the Live Flashdisk over the the external drive but all I saw was this:
[http://i1373.photobucket.com/albums/ag385/Turokei/IMG_0880_zps08wzxc7z.jpg](http://i1373.photobucket.com/albums/ag385/Turokei/IMG_0880_zps08wzxc7z.jpg)
Does anyone have any suggestion on what to do? just like that screenshot I'm in the dark

---

### Post by ajgreeny on 2016-06-09
Please do not include large images inline in future, as you did in this post.  Not everybody has a fast web connection and such images may deter some from even viewing the post.

Either attach the images by using the paperclip icon in the toolbar and navigating to the image on your disk, or simply add the http link to ypour post as I have now done for this one.

Many thanks.

---

### Post by oldfred on 2016-06-09
I do not know Mac, not exactly how they boot.
But I understand your install should be UEFI.
And external drives all boot from /EFI/Boot/bootx64.efi in an ESP - efi system partition FAT32 with boot flag.

Did you install in BIOS boot mode on external or UEFI?

For UEFI:
And grub only installs to the ESP on sda, or not the external drive and not to /EFI/Boot/bootx64.efi. For my PC UEFI full install to a flash drive I manually copied /EFI/ubuntu on sda's ESP to flash drive's ESP. Then copied it again to /EFI/Boot and renamed shimx64.efi to bootx64.efi. I then updated fstab to have correct UUID for ESP.

The version of grub in a full install is hard coded to find the rest of grub in /EFI/ubuntu so both are requried. There are ways to directly install grub as bootx64.efi, but then you have to manually maintain grub.cfg.

---

### Post by Turon on 2016-06-09
Is there a difference between EFI and UEFI? and what's ESP?

---

### Post by QDR06VV9 on 2016-06-09
As far as I have been told by people I feel as credible for Information it goes something to this effect.
EFI was developed by Intel and is specific to certain proprietary hardware. UEFI is developed by an industry-wide organization and is more open to all hardware platforms.

---

### Post by oldfred on 2016-06-09
Mac was first consumer computer with EFI and it was updated to UEFI. 
Not sure what version your Mac has, but most threads have said Mac were 1.x with many updates from 2.x and Windows started using UEFI 2.x. 

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Turon on 2016-06-09
My iMac appears to be the "Core i5" 3.2 27-inch (Late 2013) and from what I've seen it's EFI.

---

### Post by QDR06VV9 on 2016-06-09
I am just passing through but if you want to know for sure use:
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
``` From booting Ubuntu
It will return what was used IE: BIOS, UEFI. EFI
> and what's ESP?
Short for Encapsulating Security Payload, the ESP header is designed to provide a mix of security services in IPv4 and IPv6. ESP may be applied alone, in combination with the IP Authentication Header (AH), or in a nested fashion. The ESP header is inserted after the IP header and before the upper layer protocol header (transport mode) or before an encapsulated IP header (tunnel mode). ESP is used to provide confidentiality, data origin authentication, connectionless integrity, an anti-replay service, and limited traffic flow confidentiality.

---

### Post by Turon on 2016-06-09
Would I have to reinstall Ubuntu and run boot repair in the Live USB Installer?

---

### Post by oldfred on 2016-06-09
With UEFI:
ESP - Efi System Partition

Do not know enough about Mac to know even how they boot. I see many use rEFInd which is a fork and update to refit.
[http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/](http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/)
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by LostFarmer on 2016-06-10
> Ultimately I just cloned the EFI partition on the Live Flashdisk over the the external drive  That is not the correct way but might get it to work for now.  I have never tried but looking at the two files in the EFI folder of a Live ISO, it would need also the directory and contains  "/boot" from the same Live ISO copyed to the same partition.  You will also need to correctly edit /boot/grub/grub.cfg.  I do not currently have ubuntu installed and can not say just what is needed for a installed ubuntu's grub.cfg  menu entire.

when done you need in the external usb's EFI partition 2 folders below--
(EFI Partition)/EFI/BOOT/ BOOTx64,EFI and  grubx64.efi
(EFI Partition)/boot/grub/grub.cfg (edited cfg file) and other files with folder /x86_64-efi 

The above assumes that the comp is booting to the USB drive, not the internal drive.

---

### Post by Turon on 2016-06-10
How will copying files around Ubuntu do anything? OS X can't view ext4 volumes but can it boot them by simply altering boot related files in a already installed Ubuntu?

Oh and about the EFI partition I mean it was on the Ubuntu live flashdisk and I cloned it to the external hard drive. I didn't resize it at all. That's not even where Ubuntu is installed, I just hoped I could use it as a boot loader. It is the partition higher that the ext4 Ubuntu partition which has a mount point of /.

---

### Post by oldfred on 2016-06-10
The ESP - efi system partition is FAT32 and it just has initial boot files, but they load necessary drivers for whatever system you are booting. With grub much more is in the actual install including grub.cfg or menu.

---

### Post by Turon on 2016-06-10
So can I set up a EFI partition to boot Ubuntu without having to wipe the Mac's internal drive?

---

### Post by LostFarmer on 2016-06-10
On you first post looking at the photobucket link, can not see it very good but it does show it is trying to boot into grub but fails.  Thee are several stages needed for grub to boot.  For the first stage the comps firmware needs to be told where it is , that happens correctly, the location for the next stage is programed into the file of the currently running file, that location is not correct due to your cloning and not installing grub.  The stage/files not being found is /boot/grub/x86_64-efi , so copying the files from the live usb to the intalled usb hdd might do the trick, but not sure of the partition that is needed.



> So can I set up a EFI partition to boot Ubuntu without having to wipe the Mac's internal drive?           You do NOT need to wipe the internal drive.  It would help use to help you if you would post the layout of current hdd partitions.  There are many ways to do it.

in a terminal run ' sudo parted -l ' (-l is a small L)

---

### Post by Turon on 2016-06-10
Okay this is the partition layout of my computer (by the way sorry I'm not understanding very well)

Model: ATA APPLE HDD ST1000 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                 Flags
 1      20,5kB  210MB   210MB   fat32        EFI System Partition  boot
 2      210MB   1000GB  1000GB  hfs+         Macintosh HD


Model: StoreJet Transcend (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system     Flags
 1      616GB  616GB   210MB   primary  fat32
 2      616GB  999GB   383GB   primary  ext4            boot
 3      999GB  1000GB  1023MB  primary  linux-swap(v1)

The reason I suggested the possibility of wiping the internal was because of [this tutorial on ask ubuntu.]("http://askubuntu.com/questions/563401/efi-boot-ubuntu-14-04-on-a-mac-without-refind")

---

### Post by oldfred on 2016-06-10
I think everything I have seen, is that there are some things with Mac you can only do with its software. Best to never erase it.

Your flash drive is MBR(msdos) partitioned, better to use gpt partitioning. Gpt is the standard for UEFI boot, although the Ubuntu installer is often MBR. But some systems only boot flash drive if gpt in UEFI mode and some will boot MBR.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

I do not know how to partition & format with a Mac. With my PC I have normally used gparted from live installer.

 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by LostFarmer on 2016-06-11
Note: the only MAC I have used is a MacBookPro early 2011 and only messed with it for a couple months early this year. What worked for me, may not work on your Mac.

I agree with 'oldfred'  with making the usb drive partitioned as GPT vice MBR.  That is unless you plan on installing MS Windows, (my Mac , MS Windows 7 nor 10 would install in EFI mode).

Do you have a reason not to use the first 600 g of the hdd ?   

Do you want  to use GRUB menu for both Linux and Mac OS ?   It would be more problems with the external linux hdd but with more work can be done , but not needed.  Would have to have a dedicated  partition for GRUB on the internal hdd.  Do not confuse it with what is called a dedicated boot partition, that is different.

Reading the install link you posted,  it is not the way I installed on my Mac on the internal hdd.   I basically used the normal method for a non Mac to install.

---

### Post by Turon on 2016-06-11
Well about the empty space... I was trying to set up a Windows and Linux multiboot the sizes of the partitions can be subject to change. You say GPT would make Ubuntu bootable? it'll be bad for Windows though won't it? Aso I don't specifically want the grub menu to boot Ubuntu, all I want at this stage is to be able to boot Ubuntu without needing to also plugin a rEFind flash disk (as I mentioned earlier I couldn't install rEFind directly to the Mac). Hang on a second GPT is unsupported by Windows 7 and Older so my Windows 10 should be fine.

---

### Post by LostFarmer on 2016-06-11
>  it'll be bad for Windows though won't it?  Can not say for your Mac.  On my older Mac , MS Windows could not read the needed comps firmware EFI boot data, so the only option for me was a hybrid partitioning,  Hybrid partitioning is not recommended.  

You need to do a search if your model/year is MS Windows capable, to decide how to partition the external hdd (GPT/MBR).  Remember that MS Windows will only install in the mode the hdd is partitioned in.    

Just reread your first post, if you can boot into the installed linux on usb hdd with rEFind  , can try to reinstall grub correctly.  But first must know if rEFind is booting ubuntu in EFI or legacy mode.  Boot into the usb linux and in a terminal run " ls /sys/firmware/ "  , is EFI listed ?   if so you are booting in efi mode.  (have never used rEFind)

from my comp:
```
dad@debian:~$ ls /sys/firmware/
acpi  dmi[COLOR=#0000cd]  efi[/COLOR]  memmap
```

basic steps would be only if booted in EFI mode:
1) make directory ' /boot/efi'
2) mount the external FAT32 partition  at the above made directory
3) install grub.

I posted the above basic how-to only due to I might not be on again till tomorrow.

---

### Post by maestrobwh1 on 2016-06-14
I found this whole issue tiresome for years.  EFI dual booting both in PC and MAC seems cumbersome and annoying.  My MAC AIR is actually easier to dual boot than one of my Windows 10 machines.  

My workaround for MAC:

I generally prepare a boot disk with unetbootin rather than the Ubuntu usb disk creator.  The disk created via unetbootin shows as an option and its /boot/grub/grub.cfg loads when the "EFI BOOT" option is selected so I just find the uuid of the Ubuntu/nix and then add this as the first boot option.  It goes something like adding this:

```
menuentry "Ubuntu installed to disk" {
	search.fs_uuid 47f2aa22-edbb-45f7-9470-e5f105e09532 root 
	set prefix=($root)/boot/grub
	configfile $prefix/grub.cfg
}
```

Where the uuid is for the partition where Ubuntu is installed.

This works nicely, as you can install Ubuntu with the stick, choosing the boot partition to install grub (block device), then after the install before exiting, so something like the following.

Note, one can use "nano" as an editor in lieu of gedit, or in Lubuntu one can use leafpad, or in Kubuntu, use kate.
My process:

```

sudo mount -o remount,rw /isodevice

```
```
ls
```
(output should be several directories indicative of the directories on the usb installer partition/drive.)  Again, this might be /cdrom.  Look both places.
```
sudo gedit boot/grub/grub.cfg
```
notice the absence of the forward / before boot, since you are already in the directory
copy the above code for a menu entry
arrow down in the grub.cfg that opened in gedit and bump down the first menu item, then paste the menu entry code
open another tab in terminal
```
sudo blkid -c /dev/null
```
note the uuid for the device you installed Ubuntu on, copy it via the edit menu, go back to the editor,
delete the uuid from the code you pasted in grub.cfg and then paste the uuid for your device
The overall result will look like (I adjusted the "set timeout" to 5):

```

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi
set timeout=5
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
menuentry "Ubuntu installed to disk" {
	search.fs_uuid 47f2aa22-edbb-45f7-9470-e5f105e09532 root 
	set prefix=($root)/boot/grub
	configfile $prefix/grub.cfg
}
menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

```

save it.

Reboot, hold "alt" until boot options show, and it should be there again, select the "EFI BOOT" option, then the list of Ubuntu options should be there, along with the one you added, in this case the first one.

It seems to hang a bit, so be patient.  it seems to take some time locating the partition (much less than a minute though), but it does work.

---

### Post by Turon on 2016-10-20
I hope my response hasn't come too late by now. Where and how do you inpliment the first code you showed me? I did not find a file by the name of grub.cfg in the directory you mentioned, not even after pressing ctrl h to reveal hidden files.

---

### Post by Turon on 2016-11-02
I suppose it's just impractically difficult then... Is there a way of cloning reFind to my external hard drive so I don't have to plug in another flashdisk with it installed?

---

