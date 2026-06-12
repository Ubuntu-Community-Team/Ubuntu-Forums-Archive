---
title: "Multisystem LiveUSB MultiBoot using rEFIt, rEFInd mac boot manager not working."
date: 2013-10-09
forum: Any Other OS
---

### Post by Mi11z on 2013-10-09
Hello again Ubuntu forums. It's been a while.

I've left it a while since I last tried to address this. Basically I am trying to run a live usb with multiple OS's on it, on my mac. My best experience of doing this on PC in terms of convenience, features and time usage came from the likes of LiveUSB MultiBoot from a french developer which now even has it's very own distribution! See link below:[URL="http://liveusb.info/dotclear/"]

http://liveusb.info/dotclear/[/URL]

Now where I've hit a roadblock comes in the form of this. Although nowhere or anyone has ever claimed that Multisystem does work on Macs. When you run the app there is a link contained to rEFIt, rEFInd's predecessor. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246841&d=1381344252[/IMG]

This link being there implies to me that it can be done or else why include a boot manager which is only for mac's in the first place.
Please see below link to rEFInd: 

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Now I expect that the more experienced of you among the forums will tell me to just use the Mac's default "diskutil" and "sudo dd" to create a mac bootable live USB. But please consider this. As far as I know you can't "sudo dd" more than one live OS to a flash drive with this method, am I correct? 

Secondly I would just prefer using Multisystem anyway because, I like it, I'm used to it and comes packed with features. Like the ability to add and remove live OS's / distro's whenever you like, without formatting!

To finish. I would like you to note that after updating my mac rEFInd has stoping working altogether (doesn't show at boot) and I haven't yet got around to sorting it out. Also I e-mailed thedeveloper of rEFInd to ask whether or not it does in fact support Multisystem live USB's. However the ignorant or possibly very "busy" Mr. Roderick W. Smith never, ever responded!
 

Thank you for taking the time to read this, let's hope we can somehow move forward with it.

- best regards

- Mi11z

---

### Post by oldfred on 2013-10-13
I have not used Multisystem as I created my own booting with grub2's loopmount. 
And I do not know Macs. They uses UEFI but an old version that is not really compatible with the new UEFI that Ubuntu uses. 
I think rEFInd is probably your best choice as it is a boot manager that works with Mac. UEFI and grub are both boot managers as they give you a choice on what to boot, but grub also is a boot loader for Ubuntu and other Linux distributions.

This refers to booting with a Mac. If you can get the Mac to boot into a grub menu then you should only need the loopmount commands?? Not sure if they then work on a Mac or not.

 Boot ISO directly from USB efi
[http://forum.tinycorelinux.net/index.php?topic=13445.15](http://forum.tinycorelinux.net/index.php?topic=13445.15)

 Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)

 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)

---

### Post by Mi11z on 2013-10-13
Thank you oldfred.

I will get started on going through your suggestions tomorrow.

- regards
- Mz

---

### Post by Mi11z on 2013-10-15
> **oldfred said:**
> I have not used Multisystem as I created my own booting with grub2's loopmount. 
And I do not know Macs. They uses UEFI but an old version that is not really compatible with the new UEFI that Ubuntu uses. 
I think rEFInd is probably your best choice as it is a boot manager that works with Mac. UEFI and grub are both boot managers as they give you a choice on what to boot, but grub also is a boot loader for Ubuntu and other Linux distributions.

This refers to booting with a Mac. If you can get the Mac to boot into a grub menu then you should only need the loopmount commands?? Not sure if they then work on a Mac or not.

 Boot ISO directly from USB efi
[http://forum.tinycorelinux.net/index.php?topic=13445.15](http://forum.tinycorelinux.net/index.php?topic=13445.15)

 Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)

 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)


Hello again Fred,

Could I please have some more information on loopmount commands in grub/2 I've never used them/it before?

Thanks,

- regards
- Mz

---

### Post by oldfred on 2013-10-15
Found this which may be closer to your configuration. Everything else is PC based which is not the same.
 How To: Boot PowerPC live/desktop ISOs via grub2
[http://ubuntuforums.org/showthread.php?t=2051337](http://ubuntuforums.org/showthread.php?t=2051337)

 Standard flash drive with a Mac.
Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac
[http://ubuntuforums.org/showthread.php?t=2174630](http://ubuntuforums.org/showthread.php?t=2174630)

This has instructions and link to many examples with a hard drive where  (hdX,Y) may vary. Usually with flash drive it is always (hd0,1) as boot  drive is hd0 and you only have one partition.
This will boot an ISO from a PC hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

But I do not know if you boot with grub-pc(BIOS) or grub-efi(UEFI)  when using rEFInd on a Mac. The standard PC USB installer is configured for both BIOS boot with syslinux and UEFI boot with grub2. And how you boot installer is how it boots. 

Install grub to MBR of flash drive for PC, again not sure if it works with a Mac
      
 Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

 [https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)
      
 Examples:
Label partition - if label is grub2 & mount at sdb:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labelled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

If you have to have efi, again for PC and you have to change for a Mac:
      
 Bootable UEFI USB Key 
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
If you are unable to launch UEFI Shell from the firmware directly using any of the above mentioned methods, create a FAT32 USB pen drive with Shell.efi copied as (USB)/efi/boot/bootx64.efi . This USB should come up in the firmware boot menu. Launching this option will launch the UEFI Shell for you.
Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)

With UEFI you can just copy efi boot files into the folder and UEFI will boot. You can also install rEFInd into your flash drive.

---

### Post by AnttiT on 2014-05-11
Dear  Mi11z, did you succeed in the end? Also I'd like to know how to do it.

---

### Post by Mi11z on 2014-05-11
> **AnttiT said:**
> Dear  Mi11z, did you succeed in the end? Also I'd like to know how to do it.

Thanks for your interest. Unfortunately no I haven't digested all of the info yet and have been busy at work. I will get to this eventually. You are welcome to have a go yourself. For now I'm happy as long as the thread stays up so I can refer back to it of course.

Thank you all, will reply later.

---

### Post by AnttiT on 2014-12-26
> **Mi11z said:**
> Thanks for your interest. Unfortunately no I haven't digested all of the info yet and have been busy at work. I will get to this eventually. You are welcome to have a go yourself. For now I'm happy as long as the thread stays up so I can refer back to it of course.

Thank you all, will reply later.

I had few minutes to play with this again, and was almost successfull. By booting this macmini2,1 from a CD containing PLOP Boot Manager ([http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)), I was able to start GRUB on a MultiBoot USB memory. Where the good luck stopped, is GRUB as it doesn't detect my keyboard. Therefore, after a 20 sec timeout, it ends up booting the first disto on the GRUB menu. Once the distro is up and running, the keyboard works again.

Based on a quick Googling, this keyboard issue seems to quite common, though, so maybe I'll find instructions on fixing it...

---

### Post by oldfred on 2014-12-26
Do not know Mac, but on PC both Windows & Ubuntu seem to have their own keyboard & mouse drivers. But grub uses BIOS or UEFI settings. On my PC, I had to turn on BIOS settings for USB ports to use mouse & keyboard in grub. Have seen others where there were different USB port settings that had to be changed.

Does a Mac have UEFI settings for USB ports to turn them on or enable mouse & keyboard?

My newer PC UEFI system also had settings to allow USB ports to be used during booting. Some sort of security setting to prevent unauthorized users from booting.

---

