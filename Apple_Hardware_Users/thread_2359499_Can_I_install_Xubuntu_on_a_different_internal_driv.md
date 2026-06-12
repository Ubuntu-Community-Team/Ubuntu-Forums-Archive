---
title: "Can I install Xubuntu on a different internal drive to the boot drive?"
date: 2017-04-24
forum: Apple Hardware Users
---

### Post by themusicman on 2017-04-24
Hi All

I successfully installed Xubuntu on an old (2006) MacBook today, with zero experience of Linux... and I am delighted.  it also seems to be running a lot faster than the version of OSx I have on that machine - despite only having 1MB RAM! I really am pleased, I mean incredibly pleased!

So, this has given me food for thought and I am considering installing Xubuntu (or even full Ubuntu - not sure) on my main MacBookPro machine... but on a separate HDD which I have on the machine as a replacement for the optical drive I rarely used.

So my questions to you good folk are these;

1 - Can I install Xubuntu on a totally different HDD (*but located inside my MacbookPro*) and use the same software to select a dual boot? (rEFIned)
2 - Do you suggest I install **Xubuntu** *(which I installed today on the old Macbook)* or should I install **Ubuntu**?
3 - on the www site it says you can run Ubuntu 'alongside your existing OS', I'm not sure what this means other than a dual boot system. Are there other 'boot' alternatives to dual boot that I may not be aware of? (*cannot see that there are, but I guess I should ask nonetheless*) 

Your thoughts would be appreciated.  Thanks all!

---

### Post by themusicman on 2017-04-25
Hi All

Wondering if Ubuntu can be successfully installed on an external USB drive AND made selectively bootable?  By this I mean on a Mac, to choose which drive one boots from at startup is achieved by pressing the 'Alt' key during startup when you're then presented with the bootable volumes connected to the machine to choose from.

I have a 160GB external USB HDD and am wondeing if this type of installation is possible with Ubuntu?

Thanks

---

### Post by ajgreeny on 2017-04-25
Is this query specifically related to Mac hardware only or are you needing and wanting to use this external installation on other machines, including Windows, Mac, and perhaps even Linux?

---

### Post by themusicman on 2017-04-25
> **ajgreeny said:**
> Is this query specifically related to Mac hardware only or are you needing and wanting to use this external installation on other machines, including Windows, Mac, and perhaps even Linux?

It's Mac hardware only! I will only want to use this external HDD with Mac hardware.

Specifically what I am after is when booting my MacbookPro, if I do nothing and leave thr Mac to boot as I would usually do I want the machine to boot normally into OSx, but if I press 'Alt' during the boot startup process this will then allow me to select which drive I wish to boot the machine from, and I will then choose the HDD with Ubuntu on it, and boot to that.

Hope that makes sense.

---

### Post by ajgreeny on 2017-04-25
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit for this query.

---

### Post by gsahli on 2017-04-25
Get Unetbootin - it creates a bootloader on the disk - which is what the Mac looks for when you hold the Option key.
[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos)

---

### Post by themusicman on 2017-04-25
> **gsahli said:**
> Get Unetbootin - it creates a bootloader on the disk - which is what the Mac looks for when you hold the Option key.
[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos)

I'm not sure this is what I need! I used that application to create a bootable USB stick or when I installed Xubuntu on my **Macbook** recently.  What I want to do now though, is to create an installation of Xubuntu/Ubuntu on an external 200GB HDD that I can plug in to my **MacBookpro** when I need/want to use Ubuntu.  if it is plugged in, and I don't press Option key, I don;t want to have to enter a boot selector.

Is that possible with this app?

---

### Post by gsahli on 2017-04-25
I like MATE or Xubuntu myself. Yes you can have dual boot - MacOS and ubuntu, using rEFInd.
[https://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](https://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)
(but please ignore and don't try CleanMyMac3!!!)

---

### Post by themusicman on 2017-04-25
> **gsahli said:**
> I like MATE or Xubuntu myself. Yes you can have dual boot - MacOS and ubuntu, using rEFInd.
[https://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/](https://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/)
(but please ignore and don't try CleanMyMac3!!!)
Thanks, I spotted your reply to my other thread too!

The thing is, I don't want to dual boot... my understanding is that when dual booting, one has to choose which option one wants each time the machine is restarted and this is not what I want.  I only want to dual boot if the external HDD is plugged in, if it isn't then I want to start as normal into OSx.

---

### Post by oldfred on 2017-04-25
That is what booting from an external drive is.
When plugged in, you get the boot options from external which should include the internal installs.
But when external not plugged in, you should only get boot options from internal drive. 
You normally set external drive as first in boot order, and internal as second. So when external not seen internal boots.

But Ubuntu's grub makes it difficult for UEFI systems and Macs are EFI/UEFI.
And UEFI only boots external from /EFI/Boot/bootx64.efi which grub  does not normally make. 
So often have to copy/move some files around to make it work.

Do not know Mac, so not familiar with details, but you need to gpt partition in advance, and have an ESP - efi system partition on external drive.
Whether flash drive or external drive should not matter, procedure should be same.

 [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187) 
      
 Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528)
[URL="https://help.ubuntu.com/community/MacBookPro12-1/Wily"]https://help.ubuntu.com/community/MacBookPro12-1/Wily
[/URL]
 EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi) 

[URL="https://help.ubuntu.com/community/MacBookPro12-1/Wily"]
[/URL]

---

### Post by oldfred on 2017-04-25
Duplicate thread, please do not create duplicate threads on same topic.
Merged since both have posts.

---

### Post by themusicman on 2017-04-25
> **oldfred said:**
> That is what booting from an external drive is.
When plugged in, you get the boot options from external which should include the internal installs.
But when external not plugged in, you should only get boot options from internal drive. 
You normally set external drive as first in boot order, and internal as second. So when external not seen internal boots.

But Ubuntu's grub makes it difficult for UEFI systems and Macs are EFI/UEFI.
And UEFI only boots external from /EFI/Boot/bootx64.efi which grub  does not normally make. 
So often have to copy/move some files around to make it work.

Do not know Mac, so not familiar with details, but you need to gpt partition in advance, and have an ESP - efi system partition on external drive.
Whether flash drive or external drive should not matter, procedure should be same.

 [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187) 
      
 Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528)
[URL="https://help.ubuntu.com/community/MacBookPro12-1/Wily"]https://help.ubuntu.com/community/MacBookPro12-1/Wily
[/URL]
 EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi) 

[URL="https://help.ubuntu.com/community/MacBookPro12-1/Wily"]
[/URL]

I must misunderstand then.  I can press the Option key on a Mac during restart and it will then present me with all the connected or available drives from which I can boot.  I don't need to install any additional software for this to happen, I simply press Option at restart and hey presto!

I don't want to have to install anything on my MacBookPro, simply wish to know if I can create a removable bootable HDD with Xubuntu on it, that I can insert when I want to boot into that.  No addional software, just press Option and the Mac presents me with that external HDD.

---

### Post by themusicman on 2017-04-25
> **oldfred said:**
> Duplicate thread, please do not create duplicate threads on same topic.
Merged since both have posts.
Don't agree with you on this matey! Your call for sure, and that's fine, but they're not duplicate posts. I've owned my owm near-million post forum, and been around other forums long enough to know not to duplicate posts and I do try my best not to. There were additional questions on the other post that are not in this one that now may not get answered.

I am still confuzzled though re the dual boot thing!

I don't want to install any software on my MacbookPro.  On the Macbook I've installed Xubuntu on, each time I restart it, it enters the rEFInd and GRUB dual boot modes, regardless of what I want to do.  All I want to do on my MacBookPro (*yet to install Xubuntu on*) is only present me with the bootable drives when I press Option during restart, never at other times - wether the external HDD is connected or not.

Just can't get my head around this beauty... lot's of learning and reading to do!

---

### Post by themusicman on 2017-04-25
Update for anyone following 

ive installed Ubuntu onto a 160Gb hdd and tried this with my MacBookPro.  Whilst pressing Option at startup, no additional bootable drives are presented to me. I can only boot as normal. I go to sleep a sad man this evening. 

The challenge continues...

---

### Post by oldfred on 2017-04-25
Still do not know Mac, but all UEFI systems boot from /EFI/Boot/bootx64.efi. 
That is the same file that the installer uses, just that the version of grub in the installer is a limited version with just what the installer needs.

If you did full install, did Ubuntu create a new folder in your ESP on internal drive. /EFI/ubuntu?
Copy that twice to ESP on external drive, second time to /EFI/Boot and rename grubx64.efi to bootx64.efi. That version of grub expects more files in /EFI/ubuntu so both copies needed.
Then your system should be able to find a bootable UEFI system on external drive.

---

### Post by themusicman on 2017-04-26
> **oldfred said:**
> Still do not know Mac, but all UEFI systems boot from /EFI/Boot/bootx64.efi. 
That is the same file that the installer uses, just that the version of grub in the installer is a limited version with just what the installer needs.

If you did full install, did Ubuntu create a new folder in your ESP on internal drive. /EFI/ubuntu?
Copy that twice to ESP on external drive, second time to /EFI/Boot and rename grubx64.efi to bootx64.efi. That version of grub expects more files in /EFI/ubuntu so both copies needed.
Then your system should be able to find a bootable UEFI system on external drive.
Thanks for persevering with me on this one, really appreciated.  Here's the latest - and I really don't yet understand how this all works and fits together, here goes.

**Restarting using OSx boot selection function: i.e. pressing Option during restart**
With the HDD insterted, when I restart on either machine using the Mac OSx boot function i.e. pressing Option key when restarting - brings up no additional bootable drives to select, I see only the usual internal system drive of the Mac on which OSx resides.  This happens on both my Mac machines when pressing Option during restart.

[B]Restarting and doing nothing on MacBook
[/B]With the HDD insterted on my **MacBook** (*the machine I installed Xubuntu on a partitioned part of the internal drive*) when I restart and do nothing, I get presented with the rEFInd boot screen, can choose Xubuntu or OSx and continue to either.

**Restarting and doing nothing on MacBookpro**
With the HDD insterted on my **MacBookpro** (*Xubuntu NOT installed*) when I do a restart and do nothing, the Mac boots normally into OSx.

Now to your questions:
1 - I did what I consider a full install of Xubuntu onto the external HDD.  Sorry, I am not sure what ESP stands for and so can't check for it on internal drive?

2- The process of installing Xubuntu I have followed states that the HDD upon which I install it needs to be formated FAT32. Though FAT32 is supposed to be readable by OSx, for some reason this drive is currently unreadable by OSx - so now whenever I insert the external HDD with Xubuntu on it into either machine with OSx running, I am unable to read anything on it. So do I do what you suggest re copying the new folder - when in Xubuntu?

The saga continues... :)

---

### Post by oldfred on 2017-04-26
Are we mixing full install with live installer?
Live installer requires FAT32. Normally an entire 2GB flash drive. Most installers erase entire drive.
Full install would require one 300 to 500MB FAT32 to use as ESP - efi system partition. And minimal / (root) as ext4 and if new 17.04, it does not now require a swap partition where older versions did.

This is a full install on my 32GB flash drive with a data partition. You would not need bios_grub as that is only required for BIOS boot. I really do not need it either. Shows my ESP & / also.

```
Disk /dev/sdc: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      20.5kB  500MB   500MB   fat32        esp_usb  boot, esp
 2      500MB   501MB   1049kB                        bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         data32   msftdata

```

---

### Post by themusicman on 2017-04-26
> **oldfred said:**
> Are we mixing full install with live installer?
Live installer requires FAT32. Normally an entire 2GB flash drive. Most installers erase entire drive.
Full install would require one 300 to 500MB FAT32 to use as ESP - efi system partition. And minimal / (root) as ext4 and if new 17.04, it does not now require a swap partition where older versions did.

This is a full install on my 32GB flash drive with a data partition. You would not need bios_grub as that is only required for BIOS boot. I really do not need it either. Shows my ESP & / also.

```
Disk /dev/sdc: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      20.5kB  500MB   500MB   fat32        esp_usb  boot, esp
 2      500MB   501MB   1049kB                        bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         data32   msftdata

```
 Hi Fred

I really am not sure if that's what I am mixing!  I follwed the instructions from here [https://business.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253](https://business.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253) almost to the wire except from the fact I already had a copy of Xubuntu.iso so I didn't need to download that again.  I did the rest as instructed on that site but not able to boot from that HDD using OSx Option key method.

So... what do I do?  I am at a dead end here!

---

### Post by themusicman on 2017-04-26
Right - I am going to follow the instructions here:

[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

And see where that gets me!

---

### Post by oldfred on 2017-04-26
The instructions you followed were to create the live installer version. 
That is both a live or usable system to test if it works or works well with your system and an installer to create a full install.
Live installer cannot be updated, but if persistence added (file space) then some data can be saved.

---

### Post by themusicman on 2017-04-26
> **oldfred said:**
> The instructions you followed were to create the live installer version. 
That is both a live or usable system to test if it works or works well with your system and an installer to create a full install.
Live installer cannot be updated, but if persistence added (file space) then some data can be saved.
Ok, so now we are getting somewhere.  So what do I do now to get the boot version on my HDD?

---

### Post by oldfred on 2017-04-26
Some links, not sure if all are current or not:

 [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)
[http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528)
[https://help.ubuntu.com/community/MacBookPro12-1/Wily](https://help.ubuntu.com/community/MacBookPro12-1/Wily) 
   [http://askubuntu.com/questions/765254/add-grub-menu-for-os-x](http://askubuntu.com/questions/765254/add-grub-menu-for-os-x) 
   [https://askubuntu.com/questions/907570/issue-on-booting-from-refind-using-usb-make-sure-you-have-the-latest-firmware](https://askubuntu.com/questions/907570/issue-on-booting-from-refind-using-usb-make-sure-you-have-the-latest-firmware)
Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

