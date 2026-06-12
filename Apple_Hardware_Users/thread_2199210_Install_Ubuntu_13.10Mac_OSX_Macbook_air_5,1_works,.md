---
title: "Install Ubuntu 13.10/Mac OSX Macbook air 5,1 works, just rEFIt menu to fix!"
date: 2014-01-12
forum: Apple Hardware Users
---

### Post by zircon_34 on 2014-01-12
Just installed Ubuntu 13.10 (Saucy Salamander) on my 11" mid 2012 Macbook air (5,1) running a dual boot with mac OSX 10.9.1. I would like to share some problems I had during install using a live USB. I followed this [guide]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Detailed_How-To") for the install and this [guide]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx") to prepare the live USB. I prepared a 20Gb partition for Ubuntu and installed rEFit.

what works out of the box: keyboard, wireless, trackpad, sound, camera, hybernation, fan. Battery life was 2-2h30 hours with full brightness, surfing the web and writing a libre office file.

what needs to be fixed: the rEFIT boot menu shows up 3 unknown icons for linux (see below)

[ATTACH=CONFIG]249443[/ATTACH]

I have 3 boot options for linux  a) EFI/ubuntu/MokManager.efi b) EFI/ubuntu/grubx64.efi and c) EFI/ubuntu/shimx64.efi 

I searched threads about that but did not come across a satisfying simple solution, any help is most welcome!:)

---

### Post by zircon_34 on 2014-01-13
- Filevault 2 in OSX is problematic as rEFIT won't show up at startup. So I had to deactivate it.:(

- When you resize your disk in MacOS X Disk Utility (Application>Utilities>Disk utility) to create space for Ubuntu I had to choose FAT (not the default partition). Only then the ubuntu install gave me the option to install Ubuntu along with MacOS X.
[ATTACH=CONFIG]249486[/ATTACH]
- I tried to follow to install Ubuntu along with MacOSX option but this did not work, you better prepare the partition table yourself (advanced option). As you can see on the pic below I have a first partition (sda1) where EFI is (don't touch), a second partition (sda2) of type hfs+ (thats Mac OSX) and a third partition that is my free space for the Ubuntu install. 
[ATTACH=CONFIG]249487[/ATTACH][ATTACH=CONFIG]249488[/ATTACH]

- I created three partitions (see second pic above) a) SWAP (4Gb) b) ext 4 mounted at / (10 Gb root partition for file system) and c) not mandatory ext 4 mounted at /home (6 Gb for home folder). 

-VERY IMPORTANT STEP to be able to boot later into Ubuntu, for the boot loader installation (at bottom of the window) choose the root partition (mounted on /) you just created and not the whole drive that is given as default.

- At the end of the install I shut down the computer but the keyboard light was still on, no worries, I pressed on the off button. By restarting I could boot into either Ubuntu or OS X maverick without a problem using the rEFit menu.

---

### Post by zircon_34 on 2014-01-18
Update: battery life around 3.5-4 hours (at least the battery display says 5h when charged) without any tweaks, brightness set to half. Thunderbolt-dvi connection for external screen works. Keyboard and trackpad (including two finger scrolling) work perfectly.

---

### Post by Tha Tawa'S on 2014-07-20
Hello,
I don't know if you successfully removed **shimx64** & **MokManager** from refit menu, but I did on my macbook pro 11,1 (as assumed you have already installed your 3 OS):
boot up your ubuntu OS and go to **/boot/efi/EFI/ubuntu/** directory  with command-line-tool (terminator)
then you will see all  options.. shimx64, grub, MoKmanager and others.
So, as we are never safe enough, backup this folder (as sudo ) where you want (and be sure to be able to find it if necessary. I didn't)
Next step, delete shimx64 and MokManager as sudo (still with command-line-tool)
Then reboot; you will see only 3 icons.
Last step is to **customize rEFIt**; boot up your mac OS, go to **/efi/refit/icons/** with finder, rename unknow.icns as unknow.icns_BCK,, duplicate linux.icns as unknown.icns.
At the next reboot, you will have only 3 boot options, with 3 icons Linux/Mac/Win.
Have Fun !

---

