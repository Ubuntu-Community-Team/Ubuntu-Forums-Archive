---
title: "How to return to traditional bios in ASUS K55N laptop"
date: 2013-01-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kazuya on 2013-01-03
Hello team,
 
I recently purchased an ASUS k55N laptop that comes exclusively with Windows 8. 
[COLOR=red]ASUS laptop has this secure boot thing with EFI.[/COLOR]
I use F2 to go into Bios and ESC to switch boot order.
 
_**Problem:**_
_**I cannot boot up any livecds or USB boot disks to then be able to run or dualboot a linux distro.**_
 
It seems impossible to do so with all these new laptops using the secure boot thing. My question, is 
**_[COLOR=red]Can I completely remove or disable the Windows Boot manager so I can use the traditional BIOS where I can change boot order to CDROM, USB, etc?[/COLOR]_**
 
I do not want to have to continue fighting this laptop just to install linux on it.
I cannot even boot to the CDROM drive.
 
This laptop has the AMD A8-4500 CPU with 4 gig RAM Windows 8
I looked below here [http://ubuntuforums.org/showthread.php?t=2064175](http://ubuntuforums.org/showthread.php?t=2064175)
but I do not even get the option to boot to the CDROM drive.
 
Is there a guide for making an EFI compatible Linux USB boot/live disk? I want to be able to dualboot or run linux exclusively. This secure boot thing will certainly dissuade many users.

---

### Post by oldfred on 2013-01-03
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
       
 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
    older
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

    
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings -very important with some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)


Boot-Repair has been updated.
       
 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

---

### Post by geogur on 2013-01-04
i have the same problem , i can use ubuntu on my bootable usb but cant do a direct install on my tarabite hd 8 gig ram asus . so i sent away for a usb from the linux store i know that i wil be able to install off of that .

---

### Post by kazuya on 2013-01-08
This is not the best answer, but it is the best I could do to start to help newbie users just for this laptop and may help on others as well with the Secure Boot thing. I want to thank you guys and especially Oldfred for those helpful links. I got my issue resolved except for my touchpad not working.
I also got some good hints from this link, youtube, and a distrowatch write-up. I modified it slightly below for ASUS K55N user.
 
(1) Boot in your windows 8 partition. Go to My Computer > Right Click on it and select manage option.
(2) Select Disk Management > You would notice that you have a C Drive and a D: Drive for Data along with many other partitions.
-> Select D >Create Extended Paritition > In extended create 3 logical partitions
-> 300 MB for Swap; 40 Gig for Root (/) ; 80 Gig (/Home)
(it is impossible to do the resizing directly in linux due the GPT partition limitation.)
(3) Reboot your machine and select or Hit ESC button repeatedly on bootup to go bootup
Scroll to Setup to access BIOS.
(4) Scroll to Boot Tab or Advanced and Select 
 
[COLOR=black][FONT=Arial]Boot machine while pressing F2[/FONT][/COLOR]

[CENTER][COLOR=black][FONT=Symbol]· [/FONT][/COLOR][COLOR=black][FONT=Arial]Find Secure Boot in the menu tree, ignore warnings [/FONT][/COLOR]


[COLOR=black][FONT=Symbol]· [/FONT][/COLOR][COLOR=black][FONT=Arial]Disable Secure Boot feature [/FONT][/COLOR]


[COLOR=black][FONT=Symbol]· [/FONT][/COLOR][COLOR=black][FONT=Arial]Enable legacy boot options [/FONT][/COLOR]


[COLOR=black][FONT=Symbol]· [/FONT][/COLOR][COLOR=black][FONT=Arial]Enable specific legacy devices, such as USB devices [/FONT][/COLOR]


[COLOR=black][FONT=Symbol]· [/FONT][/COLOR][COLOR=black][FONT=Arial]Save and reboot while holding down F9 [/FONT][/COLOR][/CENTER]
Ubuntu 12.10 64bit is the first distro I would boot from to install and setup partitions (created from D: drive)
 
To ensure that you boot to USB Boot Disk or DVD, be sure to Tap ESC while booting up repeatedly and then select the device.
Do not select Windows Boot manager.
I either disabled Windows Boot manager or moved the Priority Order below USB and DVD Boot.

---

