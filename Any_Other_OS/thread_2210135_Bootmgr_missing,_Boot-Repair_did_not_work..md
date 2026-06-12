---
title: "Bootmgr missing, Boot-Repair did not work."
date: 2014-03-09
forum: Any Other OS
---

### Post by Frejoh466 on 2014-03-09
So I decided to try a Linux OS because people said it's better then XP, so I got my old computer and installed Ubuntu alongside with Win XP. It took roughly 1min to do anything, so Ubuntu did use allot more resurces then XP do, so I uninstalled, it and after a while I found that lubuntu would work better on older systems. So I tried again, but when I tried to boot it with the USB (used unetbootin-windows-585) it gave me Bootmgr missing.

So I read around and found that windows repair should fix it, got the disk repaired the system. And now Windows XP wouldn't boot (just got a black screen with a mouse courser) so I installed a new Win XP to try and fix it, wasn't able to. So while the Win XP OS is completely trashed, I decided to try and at least get any Linux OS to work. But it always says the Bootmgr is missing. 

Then I tried Boot-Repair but that didn't help (if this is of any use paste.ubuntu.com/7061161). 

But after 10 hours of trying I feel like I'm not going to get anywhere without help, so anyone know how to fix this?

---

### Post by TheFu on 2014-03-09
First - welcome to the forums!

I can't tell what went wrong, but having 2 USB drives connected when trying to fix this stuff might be the issue - it could be confusing boot-repair.  Thanks for the boot-info output - EXTREMELY helpful.

You didn't mention which version of Ubuntu you were trying to install. I'd suggest 12.04 for a few more months, then 14.04 when that becomes available. There will be an update method to go from 12.04 to 14.04 skipping all the intermediate, short-term-support releases.

Also - avoid using WUBI installs. Newer systems have UEFI and that makes WUBI not workable anymore, hence it is discontinued after 12.04.  I think that is the sort of installation you attempted when you say "along side of Windows."  Obviously, we cannot be certain.


```
Number  Start   End     Size    Type      File system  Flags
1      10.7GB  63.2GB  52.4GB  primary   ntfs         boot
2      63.2GB  250GB   187GB   extended               lba
5      63.2GB  250GB   187GB   logical   ntfs
```

So - what I would suggest at this point is:
* Setup a dual boot situation, to accomplish that
* shrink sda5 by 15-20G - if it is just a data partition, this can be performed using an gparted.iso booted from a flash drive.  unetbootin or yumi are easy ways to create a multi-boot flash drive.  I prefer yumi.
* While still booted in gparted, create 2 partitions inside the extended partition sda2 -
** a) 1G for swap - format it as "linux swap"
** b) whatever amount is left (14-19G) for the linux installation - format as ext4
Note the names/numbers of the larger ext4 partition - this is where you want to install Ubuntu 12.04 - we can load lxde later to reduce the runtime resources.  Probably sda6 or sda7.

Linux systems can boot just fine from logical partitions.

A little information about the system will be useful.
* RAM amount
* CPU model
* GPU installed
Thanks. This information will let us know what we are working with to make better choices.

BTW, excellent first post! I will do what I can to help.

---

### Post by Frejoh466 on 2014-03-09
> **TheFu said:**
> First - welcome to the forums!

I can't tell what went wrong, but having 2 USB drives connected when trying to fix this stuff might be the issue - it could be confusing boot-repair.  Thanks for the boot-info output - EXTREMELY helpful.

You didn't mention which version of Ubuntu you were trying to install. I'd suggest 12.04 for a few more months, then 14.04 when that becomes available. There will be an update method to go from 12.04 to 14.04 skipping all the intermediate, short-term-support releases.

Also - avoid using WUBI installs. Newer systems have UEFI and that makes WUBI not workable anymore, hence it is discontinued after 12.04.  I think that is the sort of installation you attempted when you say "along side of Windows."  Obviously, we cannot be certain.


```
Number  Start   End     Size    Type      File system  Flags
1      10.7GB  63.2GB  52.4GB  primary   ntfs         boot
2      63.2GB  250GB   187GB   extended               lba
5      63.2GB  250GB   187GB   logical   ntfs
```

So - what I would suggest at this point is:
* Setup a dual boot situation, to accomplish that
* shrink sda5 by 15-20G - if it is just a data partition, this can be performed using an gparted.iso booted from a flash drive.  unetbootin or yumi are easy ways to create a multi-boot flash drive.  I prefer yumi.
* While still booted in gparted, create 2 partitions inside the extended partition sda2 -
** a) 1G for swap - format it as "linux swap"
** b) whatever amount is left (14-19G) for the linux installation - format as ext4
Note the names/numbers of the larger ext4 partition - this is where you want to install Ubuntu 12.04 - we can load lxde later to reduce the runtime resources.  Probably sda6 or sda7.

Linux systems can boot just fine from logical partitions.

A little information about the system will be useful.
* RAM amount
* CPU model
* GPU installed
Thanks. This information will let us know what we are working with to make better choices.

BTW, excellent first post! I will do what I can to help.


I never had 2 USB connected to the computer at the same time.  I  installed Ubunto 12.0.4 with unetbootin-windows-585, there I chose  "Ubuntu" and "12.04_Live" pressed start and it downloaded and preperded  the USB, restarted the computer and made it boot with the USB then I got the option  if I wanted to try the OS or install it (first I tried it, it was slow,  but I thought it was because I run it through a USB). I then had, the  chose of "Install it alongside with Win XP", Install Ubunto and remove  any other OS, or install it on a other partition (this was when I booted the computer with the USB). I installed it alongside win XP, it was really slow and on 100% load in idle.

This I'm not sure about (might just be because it's late),
```
Number  Start   End     Size    Type      File system  Flags
1      10.7GB  63.2GB  52.4GB  primary   ntfs         boot
2      63.2GB  250GB   187GB   extended               lba
5      63.2GB  250GB   187GB   logical   ntfs
```

But I know this,
```

Disk 0/232,88GB
Number/Name Capacity          Type
1           10GB           
2/(C:)     48,83GB      ntfs     Primary
5/(D:)     174,04GB     ntfs

```

I got this info from the Win XP Disk Management. I have no problem purging the whole harddrive, becuse my original Win XP OS is currupt and no vital information is on the harddrive. So I got 232,88GB that I can partition, I used C: as OS and programs and D: for storing of information.

This is an nettop (Why? because everyone makes mistakes), so I decided to try Ubunto on an computer that I don't really care about. It's an Acer.

CPU: Intel atom CPU Z520 @1.33GHz (2CPUs)
RAM: 2GB
Video memory: 8 MB
GPU: Can't really remember, but might be Graphic card Acceleration 5000. (think it's an GPU on the CPU, and not an dedicated graphic card)

I did some searching and found that Ubuntu is more resource heavy then XP and that the lubuntu might be better for older system. It's first time I'm diving in to the Linux system due to Microsoft.

And thanks for the help.

---

### Post by oldfred on 2014-03-09
If you have XP, you should not get bootmgr missing as that is for NTFS partitions with Vista or later. If XP is not booting it should be ntldr missing message.
Did you run chkdsk from Windows 7 on your XP install? I have done that and it converted NTFS partition boot sector to Windows 7 type and I had to use Windows to convert it back. You can just run chkdsk from XP or from Windows 7 with bootsect.exe.
 [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

You are not showing any Linux partitions, so there is no Ubuntu install unless you installed with wubi inside XP. Install takes a while especially on an older system depending on Internet speed if also updating during install.

---

### Post by Frejoh466 on 2014-03-10
I have run "chkdsk" it found a problem and it fixed it, but there was no different. I can login with the second windows install (Windows.0) it's just the original windows that is broken, tho I don't really care about that, and just want to try to get Ubunto to work (Or lubunto or what OS my system can handle).

But if I installed Ubunto with wubi, should I not use unetbootin or is it Ubuntu 12.04_Live that I should not use?

---

### Post by oldfred on 2014-03-10
You may have to run chkdsk several times or until it does not report a problem as it does not fix all issues on one pass.

What second Windows, I thought you had XP?
Windows only boots from one primary NTFS partition with the boot flag. And will not directly boot from a logical partition like Linux will.
All second installs put boot files in first install with boot flag.
       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Frejoh466 on 2014-03-10
> **oldfred said:**
> You may have to run chkdsk several times or until it does not report a problem as it does not fix all issues on one pass.

What second Windows, I thought you had XP?
Windows only boots from one primary NTFS partition with the boot flag. And will not directly boot from a logical partition like Linux will.
All second installs put boot files in first install with boot flag.
       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Second windows install, as in I got 2 different Windows installations on the computer. One dosn't work, and the other one is the one I'm using now. It's dual boot with Windows and Windows.

Toght that chkdsk would fix all problem at one go, but I run it until it gives me no more errors then.

---

### Post by oldfred on 2014-03-10
Moved to other OS since all Windows issues.

You may need to run chkdsk on both NTFS partitions.
You show two entries in boot.ini but both refer to the same install in sda1 or first drive, first partition.

---

### Post by Frejoh466 on 2014-03-10
> **oldfred said:**
> Moved to other OS since all Windows issues.

You may need to run chkdsk on both NTFS partitions.
You show two entries in boot.ini but both refer to the same install in sda1 or first drive, first partition.

So I need a fully working Windows to be able to install Ubuntu? I don't want Windows to work because I'm trying to install Ubuntu, but it gives me the  Bootmgr missing when I try to install Ubuntu (or lubuntu because Ubuntu takes 1min to do something with and don't know if there is a fix for it).

If I need Windows to install Ubuntu can't I just reformat the whole harddrive and it would be fixed?

Edit:
Ok, I admit I'm bad at writing, and seem to easy confuse people, but here is what I want.

1. Install an Linux (Ubunto or a lighter version(lUbuntu?)) OS on the computer,

CPU: Intel atom CPU Z520 @1.33GHz (2CPUs)
RAM: 2GB
Video memory: 8 MB
GPU: Can't really remember, but might be Graphic card Acceleration 5000.  (think it's an GPU on the CPU, and not an dedicated graphic card)

---

### Post by oldfred on 2014-03-10
You are getting error message as you DVD or flash drive is not bootable. Then BIOS defaults to hard drive and gives error.
Did you verify ISO is correct?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Does your system boot from USB flash drives? Older systems with USB ports may not boot from them, only from DVDs or CDs.
      
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

    
Your systems seems like it is new enough to boot Ubuntu from flash drive.
I have a laptop from 2006 that was XP with dual core and 1.5GB that boots Ubuntu. But Unity is a bit slow, so I install flashback/fallback which uses menus. Others suggest Xubuntu or Lubuntu.

---

### Post by Frejoh466 on 2014-03-10
The computer does not have an CD/DVD reader, so it can boot from USB (thats how I installed the first OS) but it set to boot 1.USB 2.HDD. When I start the computer I get the "Press any key to boot with USB..." I press any key, it start to read the USB then I get "Botmgr is missing, press ctrl+alt+delete to restart. 

I re-downloaded Lubuntu because that seems like the OS my computer can handle because Ubuntu uses allot more resources then Win XP does, and my computer used 100% CPU in idle (first time I tried it when I didn't get the message, I get the message now because I unisnstalled it because it use 100% CPU in idle). The Lubuntu .ISO I got now have the right value, but still get the "bootmgr is missing" when trying to boot with the USB and i prepared the USB with "unetbootin-windows-585".

---

### Post by oldfred on 2014-03-10
You will not get bootmgr missing except from Hard Drive, so USB flash drive is not correctly configured.

       Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
Common USB BIOS boot options
[http://www.pendrivelinux.com/usb-bios-boot-options/](http://www.pendrivelinux.com/usb-bios-boot-options/)

---

### Post by Frejoh466 on 2014-03-11
I have used the UNetbootin. The rest gave me same the same problem, "bootmgr missing".

But the problem only exist for Linux, I can boot with the recovery disk, other OS installation disk.

There is one thing I don't understand, why do I need an other OS installed to install Linux? First time I installed Ubuntu, the installation went fine, but after I uninstalled I got the bootmgr is missing error. So that tells me the Install is ether depended on something on the HHD or the USB don't work, but the USB does work because it went fine the first time, and I can get Win XP USB install to work just fine, so I'm I missing something or why can't the Linux OS install just from the USB alone?

No changes in the BIOS where done after the uninstallation, just deleted the Ubuntu install (this is the guide I was using to uninstall Ubuntu [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/))

---

### Post by TheFu on 2014-03-11
You don't need any other OS to use Ubuntu.
You can completely wipe all prior data, if you like, and install any flavor. If you want to keep any of that data, back it up somewhere else.  We've been trying to ensure that you DO NOT loss any data. If you don't want it, wipe the disk, repartition however you like and move forward.

So - use the flash drive with the installer, and tell it to "use the entire disk" - that should wipe everything and install Ubuntu.

Netbooks aren't "bad" - they have a purpose provided you understand the limitations.  I have an old Asus Eee and just picked up a new chromebook last night.  The Eee runs Ubuntu fine - I don't use the Unity GUI, preferring LXDE, which is much lighter.
* CPU - N280 Atom
* RAM - 2G
* GPU - onboard Intel crap (no video extensions for MPEG, h.264 accel)

The Chromebook is too new  - haven't wiped it to load Ubuntu yet. That is the plan for today. The CPU on it is about 15x faster - maybe more. It is faster than a Core 2 Duo desktop (Intel E6600) I had 4 yrs ago. Still only 2G of RAM, but that is more than enough.  My main Ubuntu desktop only has 1.5G of RAM running inside a virtual machine on a Core2 Xtreme - so this chromebook should run about the same - VERY fast.  Plus the video GPU is current generation - should handle playback of 1080p stuff easily.  Just need to find a way to get 500G of storage connected to it. Currently only has 16G - which is next to useless - and it uses an ultra tiny SSD (m.2 form factor). I'll definitely be breaking the warranty on that.

---

### Post by oldfred on 2014-03-11
I thought you wanted to fix Windows.

The bootmgr error only comes from a Windows bootloader in the MBR trying to boot from a Windows partition that does not have bootmgr. That should be your hard drive.

So the issue still has to be be something with flash drive not being correctly configured or download of ISO was not correct. Or your system is very old and only 32 bit and you are trying to boot 64 bit.

Have you tried another download of Ubuntu and verified with md5sum?
Have you tried another flash drive?

---

### Post by Frejoh466 on 2014-03-11
So somehow the computer decide to load the harddrive instead from the USB as I tell it too, I got that right? But I tried both Ubuntu and Lubuntu, and verified it with md5sum after I downloaded the .ISO file (Both was 32-bit).

The information of the computer I don't care about, and can be wiped clean, this is a computer I rarely use due to the low spec, and make it only useful for light surfing. I tried 2 different USB, and I can boot with USB on Win XP USB and Linux repair USB, but when I try to boot with USB to install Linux I get Bootmgr missing. I tried reinstall win XP but I still have the problem. There is nothing important saved on the computer. So both win XP and all information on the harddrive can be wiped.

So could I could change Ubunto to not use 100% CPU power in idle? what would I lose and what is the different from Lubuntu? I don't really know what Unity GUI, or LXDE is, but I'll look around and see if I find anything.

Edit:
So I found out that the Unity, LXDE, GNOME and so on just are the "themes" for Ubuntu.

Edit2:
Problem **solved-ish **by changing USB from NTSF to FAT32 format. Tho it doesn't help that the screen goes completely black when I try to install it. Crash and an long beep sound when I try to the "Try Lubuntu" random restarts and other random errors. The md5sum is right, and I tried multiple times. I will try Ubuntu again and see if I can install it or if I get the same errors I have now, even tho my computer is way to week to handle the Ubuntu OS (or the theme).

But I no longer get "bootmgr missing" error.

Edit3:
Just to be 100% clear, my hard drive is completly empty and formated to ext4, if I try to boot with USB NTFS it tell me "Bootmgr missing" if I format USB to fat32 I get errors and unable to install Lubuntu or Ubuntu. So that means that I can't run Linux OS on my computer?

---

