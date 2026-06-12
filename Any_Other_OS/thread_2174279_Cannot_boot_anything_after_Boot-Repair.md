---
title: "Cannot boot anything after Boot-Repair"
date: 2013-09-13
forum: Any Other OS
---

### Post by vitor3 on 2013-09-13
Hey everyone,

First things first, here is the link I got after the first time I did boot repair [http://paste.ubuntu.com/6103007/](http://paste.ubuntu.com/6103007/)

And now the story: 

I got this computer with windows 8, but later I decided to install ubuntu because it was the distro I was most familiar with, a few days ago however, I decided I would like to try openSUSE, so I deleted my ubuntu partitions (which I am fairly sure cause this problem).

Anyway, after that I installed openSUSE, but it didnt appear on the boot devices list, ubuntu still did appear however, if I were to choose ubuntu (which was already deleted) it would go to a screen wich said error: invalid filesystem (or something like that) and below that there was : grub rescue> _

Well, I tried almost everything I could to get openSUSE to boot, and a few friends sent me some links, but most of them required the use of the terminal and most of those tools werent present on openSUSE live, so I made a USB with ubuntu so I could use more commands.

I started ubuntu live, tried some of the guides but half of them didnt work or said no such file or directory, and then I used Boot-Repair...


I copied the link, then I restarted, went to the boot menu.

I noticed there were 2 "new" boot devices: another Windows one (with the exact same name as the first) and another ubuntu one (making this the 3rd ubuntu boot device, with the same name and not counting with the USB)

Now, all of them would take me to the grub rescue> _   screen... in other words, I can only boot my PC through my USB using ubuntu live now...

I really would like this to be fixed... I have no idea what to do and most commands are... weird maybe?

Anyway, I'll wait for your responses, thanks again

---

### Post by oldfred on 2013-09-13
Moved to otherOS since not Ubuntu anymore.

UEFI has its own memory, so if you have old entries you may also have to remove them with UEFI menu, or with UEFI shell.
 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples $5 is delete:

Also efi partition is where boot loaders always go with UEFI. And each exists in its own folder. So unlike BIOS a new install creates its own folder and does not overwrite previous boot loaders. You still show Ubuntu folder in the efi partition.

It looks like Opensuse installed grub to a PBR - partition boot sector. That only works with chainloading from another boot loader, but I do not know if that is how it is configured. That is more common with BIOS then UEFI.

You want all installs in UEFI mode not BIOS mode. You show these in sda2.

 /EFI/Boot/
 /EFI/opensuse/
/EFI/ubuntu/
 /EFI/Microsoft/

But somehow another partition was created as FAT16 and has boot flag. The boot flag in gparted detemines the efi partition and you can only have one per drive. (Standard may allow 2, but most systems do not handle that yet.) I would use gparted and remove boot flag from sda5. Normally FAT16 was the efi format for removeable devices. Ubuntu's grub2 with very early version like 11.10 used to create FAT16, but since corrected. Maybe Opensuse is using an old version of grub2?

After removing boot from from sda5, go into UEFI menu (or one time boot key) and see if you can directly boot the systems you have installed.

---

### Post by vitor3 on 2013-09-13
Here is what I just did, I have deleted the ubuntu boot partitions using sudo efibootmgr -b #### -B. I deleted all 3 ubuntu ones (since I dont have ubuntu installed) and the extra windows one.


I believe the boot flag is on sda2 now... but before I restart my computer and test this, there are some things I'd like to make sure first, since I' on the live version.


Since I only left Windows and my USB drives as bootable options, this also means openSUSE will still be unbootable even if windows now is...


What should I do now to make "sure" I will be able to boot into windows and possibly into openSUSE?

---

### Post by oldfred on 2013-09-13
All systems if installed in UEFI mode should boot from UEFI menu. Even if installed in BIOS mode you should still be able to boot from UEFI/BIOS menu.
It just is to easily dual boot with two or more systems they must all be installed in same boot mode. All BIOS or all UEFI. And since you just about cannot convert a Windows UEFI install to BIOS, you need all the Linux systems installed in UEFI mode.

Do not know about OpenSuse. If using grub2 is should be similar to Ubuntu as it uses grub2. But BootInfo report showed grub2 installed to a partition(which would be a BIOS install). So it may be in BIOS mode, but will  not ever boot. It needs to be in MBR, you will need a bios_grub partition if BIOS booting with grub2 and would have to go into BIOS and turn off UEFI, turn on BIOS to boot. Better to convert to UEFI. Not sure if Boot-Repair can do that for OpenSuse, but it does for Ubuntu by uninstalling grub-pc and installing grub-efi.
But you also had an OpenSuse folder in the efi partition. It may depend just on which version of grub pc or efi was fixed last by Boot-Repair.

But sometimes leaving fast boot (hibernation) on in Windows creates boot issues. But that really is a separate Windows boot problem. Also any resize of Window from outside of Windows will require chkdsk from Windows.  Again that is a Windows repair and if it had both hibernation and chkdsk issues it can be a bigger issue.

---

### Post by vitor3 on 2013-09-13
hm... I will try and see if I can boot into windows now.

But the thing is, when I had ubuntu, each time I wanted to boot it I had to press F2 (on my case) to go to the BIOS menu and select ubuntu boot loader as the first one to execute, and that would allow me to choose ubuntu, windows or other things... the windows one stopped working after some time though, but doesnt matter now.

What I'm trying to say is that unless I selected ubuntu from the BIOS settings, it would boot me into windows without any prompts or confirmations...

So what do you suggest I do about openSUSE? Do I install it again and hope it will be added as well as grub to the MBR or something?

On a side note, I tried to purge and reinstall grub using Boot-Repair once... didnt work, told me to type some commands on the terminal but the said it was an invalid file or directory...


So my question is, what should I do to boot openSUSE now?



------EDIT------


I have just successfully booted into windows, however I did notice that 2 ubuntu booting options still remain though.

Now I would just like to be able to boot openSUSE in the safest way possible, and by that I mean a way that will not prevent me from booting in the future

---

### Post by oldfred on 2013-09-13
It sound like you installed Ubuntu in BIOS mode. Default boot was UEFI with Windows so you have to manually select BIOS/CSM/Legacy boot with grub2.
Not sure how you now have OpenSuse installed? It shows in BootInfo report both a BIOS type install of grub to a PBR - partition boot sector. You almost never install grub to a partition in BIOS mode as BIOS only boots from MBR not PBR. But you also show a OpenSuse folder in the efi partition. Does that entry from UEFI boot?
Not sure how you run the equivalent of sudo update-grub in OpenSuse. You need to be root and run the update-grub command.
But grub2's os-prober in Ubuntu does not create correct chain load entries. I think Debian just updated it but it is not in most or any versions of Ubuntu. And I have no idea of what version of grub2 OpenSuse uses.
With Ubuntu Boot-Repair will add correct chain load entries to grub menu. I am sure OpenSuse has similar fixes.

---

### Post by vitor3 on 2013-09-14
Hm... I'll look around the internet for possible fixes, thank you for now :)

---

