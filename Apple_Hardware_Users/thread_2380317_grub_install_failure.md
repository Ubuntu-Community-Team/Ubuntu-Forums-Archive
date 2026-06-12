---
title: "grub install failure"
date: 2017-12-15
forum: Apple Hardware Users
---

### Post by davidalden on 2017-12-15
I am trying to install Ubuntu Studio along side OS X on an older mac mini (core 2 duo) to be used as a dedicated DAW in a home studio.  I want to keep the OSX for convenience in managing music files on my iphone and ipod.

On the install, I get what appears to be a very common error message: "the 'grub-efi-and64-signed' package failed to install into/target/.  Without the GRUB boot loader, the installed system will not boot."  The installer then crashes.  I cannot get into Ubuntu Studio at all in the trial mode (says its already mounted/ or busy).  I can open a linux terminal window.

I have seen MUCH discussion on this, and there are many suggested fixes.  None of the suggested instructions is clear enough.  For example, it is suggested that I rename the x86.64 file to x86.AMD64 file....but nothing tells me how to find it or how to rename it.  I have installed the rEFInd program in the apple OS, but that did not solve the problem.  I have tried manually creating two partitions for the linux install; that did nothing.

I am hoping someone can point me to a clear description of how to solve what appears to be a common problem.

---

### Post by howefield on 2017-12-15
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by oldfred on 2017-12-16
I do not know Mac.

But older Mac do not have UEFI, but have the earlier EFI. And do not even have UEFI Secure Boot, so do not need signed packages.
But part of system not installing seems like an issue anyway.
Are you installing UEFI or BIOS boot mode. Not sure if older core2 Mac use EFI or not?

Most with Mac find rEFInd works where using grub as boot manager (menu) does not work well. But grub still is Ubuntu's boot loader.

Not sure if this works on your Mac or not.
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL]
 Mac Mini 
[http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/)
[http://askubuntu.com/questions/563401/efi-boot-ubuntu-14-04-on-a-mac-without-refind](http://askubuntu.com/questions/563401/efi-boot-ubuntu-14-04-on-a-mac-without-refind)
[http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890](http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890) 
      
 Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html) 
    


[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by davidalden on 2017-12-17
thank you...I don't understand all you are saying, but there are several things I'll pursue.  First, you're right, my older MAC mini uses an EFI, not UEFI, and I think the iso I'm using wants a UEFI...I'm researching how to make an EFI bootable USB drive.  Also, I have downloaded and installed rEFInd on the apple, but it doesn't do any good...I'm assuming I've got it in the wrong place but don't know where it should go, or how to get it there. A couple other things:  I don't have a Ubuntu Live option....when I load the iso and it runs the install, I cannot open the Try Ubuntu from the USB drive option...it always says the drive is not mounted or busy....and yet it runs the install just fine (up until the crash point around grub.) Second, I tried to get something from a ppa following terminal language instructions I got (it was probably the boot repair), and got the message that the computer couldn't find the ppa library, or resource.  But thank you for the hints....I'll read all those references before bitching any more!

---

### Post by kevin160 on 2017-12-18
Don't be too worried about "uefi" vs "efi", but make sure to follow mac guides, not general pc guides. If they don't mention rEFInd at all, you are probably looking at a PC guide.

There are a couple things that influence which guide you should follow to get Ubuntu onto your mini:

Firstly, do you want to install in "BootCamp" (aka "BIOS emulation") mode, or in EFI mode.  I like EFI mode because on my machines it supports hardware better, but BootCamp mode is simpler.  The choice is yours; just make sure you are following a guide for your particular choice.  

Secondly, is your EFI 32-bit or 64-bit?  You don't mention which Core2Duo mini you have, but if you are unlucky, you may have one of the models that only has EFI-32 even though your processor is 64-bit.  If this is you, see [Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)]("https://ubuntuforums.org/showthread.php?t=2287767") for some tips on the commands you need for installing the grub-efi-ia32 package.

In my experience, installing on a 32-bit EFI machine without taking extra steps causes ubuntu to fail it's first boot, not to fail installing grub.  I've had the ubuntu installer fail to install grub even on a standard PC because the wifi was flakey and updates failed, so say no to updates and install those after.  

One final hint that I don't often see in guides:  get supergrub2 and burn it to a USB stick or CD.  It can scan for and boot kernels even if grub isn't installed correctly.

---

