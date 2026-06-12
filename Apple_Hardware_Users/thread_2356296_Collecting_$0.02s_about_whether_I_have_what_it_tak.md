---
title: "Collecting $0.02s about whether I have what it takes to run Ubuntu"
date: 2017-03-22
forum: Apple Hardware Users
---

### Post by dhodges on 2017-03-22
Hi there. I'm new to the forum and new to Ubuntu. 

I'm hoping I can get some straight dope about what to do.

I'm sort of handy with electronic things but perhaps not handy enough. I managed to make a bootable USB and test out Ubuntu on my Mac. I say "test out" because I think I didn't really understand what I did and I couldn't get WiFi to work on my laptop (but I could on a mac mini) and I couldn't install any programs.

In my head I was creating an external USB I could use like a small ssd with Ubuntu on it. I was then going to install Inkscape (the 96DPI change is not coming to mac soon enough for the book I'm working on) and  run things off that USB.

In short, I don't know if I can make a bootable ubuntu USB with programs on it or if I should just get a windows machine. I'm worried about installing it directly on my macbook because I don't seem to have what it takes to run it from a USB.

---

### Post by &amp;KyT$0P# on 2017-03-22
Since you're new to Ubuntu, I would suggest you try it in a way that's somewhat friendly to Ubuntu-newbies.  Starting out with Ubuntu on bare-metal Apple hardware is like jumping in the diving pool before learning how to swim.

Have you considered running Ubuntu in a [VirtualBox]("https://www.virtualbox.org/") virtual machine?

---

### Post by Bucky Ball on 2017-03-22
As above, and also: to install Ubuntu to a USB, the easiest thing to do is use another USB with the Ubuntu installer on it, which it sounds like you already have created. 

When you boot the USB you have, does it have the options 'Try Ubuntu', 'Install Ubuntu', etc.? If so, you have the installer. Anything you install when running a 'live' session on that will be lost on reboot. The good news is you can use that to install Ubuntu. With a blank USB in (or a USB hard drive or whatever), simply click the icon 'Install Ubuntu' on the desktop, choose 'Something Else' and choose the blank USB drive as the target for your install.

But that's on a non-Mac install. You will probably need to learn some of the black arts with a Mac, so I have requested this be moved to where it should be, the Apple Hardware Users section of the forum. :)

Don't be too worried. Plenty of people are running Ubuntu on Macs and sure some of them will help you. It's not impossible, or even more difficult, but it is different to a regular PC install. Good luck. :)

---

### Post by wildmanne39 on 2017-03-22
*Thread moved to **Apple Hardware Users**.*

---

### Post by ajgreeny on 2017-03-22
I am a bit confused about whether you want ubuntu on your Mac-mini or on another (Windows?) laptop, so please clarify that for us before jumping in and potentially messing up an already working computer.

You also need to be careful if the computer uses UEFI rather than legacy BIOS as the bootloader files for Ubuntu will wipe out whatever is there now and should you decide Ubuntu is not for you, and remove it from the machine, you may find you can not boot to the previous OS.
Make sure you have whatever rescue disks or system are needed before jumping into what could be a very deep end for you.

---

### Post by dhodges on 2017-03-22
Thank you to everyone who has responded so far. I see where I have been confusing now. I also know the questions I need to ask.

So...
I have an old-ish macbook pro retina mid 2012 which I mostly use. I want to be able to run the newest Inkscape (.92) with the new standard 96DPI. The problem is that mac does not have this version and I don't know when it will.

In order to use this standard I feel like I have two choices: run Windows, either as bootcamp or buy a new Windows machine, or run Ubuntu on the machine I currently have.

The first option is a question for another forum and in all likelihood something I can comfortably achieve.

The second option is why I'm here.

I have already "successfully" created a bootable Ubuntu USB but as I have discovered in the comments above, this is not actually a drive I can do things from. 

In a perfect world I would like to create a bootable and "persistent" usb drive with Ubuntu on it. On this drive I'd like to install Inkscape and some other stuff. I'm open to installing it on an external HDD as well but what the USB may lack in long-term stability it makes up for with portability and, as I'm doing bite-sized chunks of work and then exporting it, if it fails I can replace it with minimal risk.

---

### Post by Bucky Ball on 2017-03-22
Well, it might be as easy as putting in a blank USB and installing from the USB you've created to the blank USB in that case. The tricky bit is expecting that USB Ubuntu install to boot on any machine. It won't. To get it to do so, you are going to need to perform definite black arts. Some machines are UEFI, others legacy, some are Macs. Your black magic USB needs to be able to boot on all of them? That is probably the most difficult part to solve of what you are hoping to achieve.

---

### Post by dhodges on 2017-03-22
Thanks for the speedy reply!

I think that I have perhaps been confusing again. I only need this to run on one machine, my mid 2012 macbook pro. I do most of my writing on it and I'd like to be able to do the little bit of vector art on it as well. 

Thanks to those that suggested virtual box. The issue there is that the resolution would be a constant frustration when working with large piece of pixel perfect vector art.

---

### Post by dhodges on 2017-03-22
So, if I understand correctly... 
I make the bootable USB on the mac I want to use the persistent USB on (done)
 Boot the USB and choose install
Choose the second separate USB I have plugged in as the target for that installation
Allow installation then I can run from the USB, install programs on it etc?

---

### Post by oldfred on 2017-03-22
I do not know Mac.

But Mac uses UEFI with gpt partitioning. 
You will need to partition in advance, so you have the ESP - efi system partition on the flash drive.
External devices only boot from the ESP using /EFI/Boot/bootx64.efi. The installer uses that file, but does not create that for full installs to external devices in UEFI mode. You just have to copy the /EFI/ubuntu folder to the ESP on the flash drive and copy again to /EFI/Boot and rename grubx64.efi to bootx64.efi. Copy of grub with full install expects more boot files in /EFI/ubuntu so both copies required. Installer version has limited version of grub that only needs /EFI/Boot folder.

       [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)
[http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac full install UEFI boot to flash drive
[URL="http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528"]http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528
[/URL]
 EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi) 

[URL="http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528"]
[/URL]

---

### Post by dhodges on 2017-03-22
So in short...no, I don't understand correctly.

Thanks @oldfred I read through those and they made me feel like perhaps I don't have the moxie for such an undertaking. I was heartened when I discovered this (which I believe is a distillation of the advice you gave in the thread you directed me to). From [http://askubuntu.com/users/589770/tom-seddon](http://askubuntu.com/users/589770/tom-seddon)

> 
[LIST=1]
[*]make folder in root of empty EFI partition called EFI
[*]copy ubuntu folder (that the installer added) into the new EFI folder
[*]make folder in EFI called Boot
[*]move EFI/ubuntu/grubx64.efi and EFI/ubuntu/MokManager.efi into EFI/Boot
[*]move EFI/ubuntu/shimx64.efi into Boot, and rename it to BOOTx64.EFI
[*]Edit EFI/ubuntu/grub.cfg, find the search.fs_uuid line, and remove the device specifier from the end (so it reads just search.fs_uuid <<GUID>> root).
[/LIST]
[COLOR=#111111][FONT=Ubuntu]My USB disk then appears in the Apple boot menu when it's connected. And when selected, it brings up the usual boot menu, and I can select Ubuntu and off it goes.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]As a final step, once up and running, I edited /etc/fstab to mount the USB disk's EFI partition, rather than the MBP's.[/FONT][/COLOR]


Does this match what you advised me of in this thread? If it does, I think perhaps it might be something i could tackle.

---

### Post by Bucky Ball on 2017-03-22
Just throwing this in: don't forget to backup your valuables before hitting the big button. :)

---

### Post by dhodges on 2017-03-22
Am I trying something really advanced or is this a pretty standard type of thing for people to do?

And... why do people hide their beans?

---

### Post by oldfred on 2017-03-22
That is essentially what I have done, but I have a PC, not a Mac.
I do not think Mac has Secure boot, so either grubx64.efi or shimx64.efi can be used. 
I normally use grub, as I do not have UEFI Secure boot on. 
I do not edit the 3 line grub.cfg in the ESP. But do back up the ESP on sda internal drive, before & after installs.
I have multiple Ubuntu installs and every one overwrites the previous /EFI/ubuntu in sda. So I have to restore the grub.cfg of my main working install 16.04.


You also should change the mount of the efi partition in fstab to the UUID of the ESP on the external drive. 
Default install will have UUID of ESP on internal drive.

A lot of Mac users use rEFInd as that is a nice graphical boot manager, where grub just has a text menu.
Grub is both a boot manager (menu) and the boot loader. With rEFInd, you still use grub to boot.
Some with PC now use that also.
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

