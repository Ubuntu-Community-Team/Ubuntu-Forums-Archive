---
title: "Error 21?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-05-16
I've installed ubuntu successfully a couple of times now on my external hdd, but the problem is that whenever I shut down the computer and then reboot it, I get this message:

Grub Loading Stage 1.5
Grub Loading please wait....
Error 21

I looked it up and Error 21 means selected disk does not exist. Any ideas on how to fix this?

---

### Post by annda on 2007-05-16
does BIOS recognize the USB disk on boot? is it connected when you reboot?

it looks like GRUB is installed on the main harddrive but needs the ext hdd to be plugged in on boot...

---

### Post by PMatt on 2007-05-16
The external hdd I'm using is plugged in on the reboot, and I had Ubuntu working.

"does BIOS recognize the USB disk on boot?"

This is probably a total noob thing, but how would I find that out?

---

### Post by PMatt on 2007-05-16
Here's what I found on Error 21, hopefully some of you can help me make sense of it:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

"I have read of this error being described after the number2 hard disk with the Linux installation on it has been removed from the machine. Grub had been installed in the MBR in the number 1 hard disk, and when the number 2 hard disk was removed, the machine could not boot anymore, and showed 'grub error 21'.

This is because bootloaders have two or three parts. The first part, called 'stage1', normally is very small, and lives in a special part of the MBR. The second part, called 'stage2', is much larger and lives in the operating system itself. Other bootloaders work the same way too.

Basically the only work the small part (stage1) has to do is to find the other, larger part, 'Stage2'.
It is 'stage2' that does all the hard work, it can because it is bigger.
In the case of Grub, there is also another part called 'stage1_5' which helps 'stage1' to find the other part.

When the hard disk that contained the operating system has been removed, Grub cannot work because the larger part of it is gone.
The first part of Grub, which is very small and whose only job is to find the larger part, gets help from stage1_5, but if the hard disk with stage2 on it is gone, they cannot find stage2 of course, so they complain by printing out this error massage.

Please put the hard disk with stage2 in it back into the machine, and/or make sure it is properly plugged in and detected and set up in the BIOS.
If you happen to be using a hard disk larger than 137 GB, see also error 18.


Other ways to solve this problem might be, (depending on your circumstances and the situation),

    * re-install Grub from an operating system that is in another hard disk that is to remain in the machine.

    * install a different boot loader or boot manager to MBR that belongs to an OS that is to remain in the machine. (re-install Grub).
    * go into bios and check if the hard drive controller is "off", if so change to "auto".

Super Grub Disk can easily and quickly install a different bootloader's stage1 to MBR of your first hard disk for you.
If it is another Linux system with Grub or Lilo, look in Super Grub Disk's Gnu/Linux for options.
If you want a Windows bootloader's stage1 written back to MBR again, look in SGD's Windows.
If your computer still has more than one hard disk, look in Advanced for menus that are designed to offer you the most options."

---

### Post by PMatt on 2007-05-16
Anyone? Please.

---

### Post by gn2 on 2007-05-16
I've found (with other distros) that booting from a USB  hard drive isn't always reliable.

Where is Grub installed to? 

I would suggest having grub on the USB drive, and the USB drive before the internal drive in the boot order.

---

### Post by PMatt on 2007-05-16
I'm pretty sure Grub is installed onto the internal drive because it doesn't matter if the external hdd is connected or not, I still get the error message. 

Is there anyway you know of to remove it from the internal hdd and put it on the external? I'll search around too, but I would appreciate just a little more help. Thanks.

---

### Post by gn2 on 2007-05-16
Here's Herman's helpful site's home page: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
All the info you'll need is in there.

Replace the Windows native bootloader using the fixmbr command from recovery console, and use a SuperGrub disc to write Grub to the USB drive, or use the Gag bootloader to boot the USB

---

### Post by ThePolemistis on 2007-05-16
> **gn2 said:**
> Here's Herman's helpful site's home page: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
All the info you'll need is in there.

Replace the Windows native bootloader using the fixmbr command from recovery console, and use a SuperGrub disc to write Grub to the USB drive, or use the Gag bootloader to boot the USB

i had this error once too... its when i removed an external HDD which contained one of the two linux OS on my system
ill do what this guy says...  but im not sure on the supergrub part... what i did was modify the menu.lst file to remove reference of my second HDD (the one i removed). You should do the same i think.

---

### Post by PMatt on 2007-05-16
Do you think using supergrub would help? I'm looking into it now, but would like some input.

---

### Post by adrian15 on 2007-05-17
> **PMatt said:**
> I've installed ubuntu successfully a couple of times now on my external hdd, but the problem is that whenever I shut down the computer and then reboot it, I get this message:

Grub Loading Stage 1.5
Grub Loading please wait....
Error 21

I looked it up and Error 21 means selected disk does not exist. Any ideas on how to fix this?

That external hard drives installations are a nightmare.

I will explain you what happens when you install Ubuntu it thinks the following thing:

1st hard disk = internal hard disk
2nd hard disk = extenal hard disk

So as long as always the 1st hard disk is the first that boots it installs grub to the 1st hard disk.

However when you reboot BIOS tries to set up and boot things and now there are two scenarios:

1 scenario) Bios boos internal hard disk as always ( I think it is your case)

1st hard disk = internal hard disk
2nd hard disk = UNKNOWN

Why? Ask your BIOS manufacturer for making so bad bios.

2 scenario)  You force BIOS to boot from the usb external hard disk.

1st hard disk = external hard disk
2nd hard disk = internal hard disk

As long as Ubuntu in the installation has not installed any grub in the external hard disk and as long as the bios tries to boot the 1st hard disk (which in this scenario is external hard disk) then NOTHING BOOTS.

So you have a kind of solution that it is forcing the installation of grub in the extenal usb drive (ask Herman for info or check its webpage) and then setup your bios that it boots from your external hard drive.

The bad thing about this is that in MOST of the BIOS you have to setup the boot from the external usb drive each time your power on the machine even each time you reboot.

adrian15

---

### Post by gn2 on 2007-05-17
> **adrian15 said:**
> That external hard drives installations are a nightmare.



I entirely agree, installing Ubuntu to a USB drive isn't easy.
PCLinuxOS  will install directly to a USB hard drive though.

Some time ago I set up my PC as a dual-boot with PCLinuxOS 0.93a installed to an external USB hard drive. 
I disconnected the internal drive before running the installer. 

This forced Grub onto the USB drive, and as Grub didn't "know" about the internal drive there wasn't a problem.

Internal drive was Windows XP and unaffected in any way by the Linux USB drive.

I've moved on since then, and now have a conventional dual-boot with Xubuntu on the internal drive. 
Windows is still there, but gets booted extremely rarely, less than once a fortnight, usually just for security updates.
Wonder why I bother keeping Windows sometimes, but I'm loathe to dispose of it because it's paid for........

---

### Post by PMatt on 2007-05-17
I had another thought. 
What if I disconnect the external hdd, and then run the live cd to install ubuntu onto the internal hdd. Would this fix the problem I've been having with Grub?

---

### Post by gn2 on 2007-05-17
> **PMatt said:**
> I had another thought. 
What if I disconnect the external hdd, and then run the live cd to install ubuntu onto the internal hdd. Would this fix the problem I've been having with Grub?

Is there a specific reason why you're trying to run Ubuntu from an external USB drive?

If not, then install Ubuntu and Grub to the internal drive with the external drive disconnected.

Have a good read of Herman's site first though.

---

### Post by PMatt on 2007-05-17
> **gn2 said:**
> Is there a specific reason why you're trying to run Ubuntu from an external USB drive?

If not, then install Ubuntu and Grub to the internal drive with the external drive disconnected.

Have a good read of Herman's site first though.

I was dual booting windows from the internal and ubuntu from the external. But like you guys said, it basically turned into a nightmare with the error 21 message and I just figured this would be a way to fix it. I don't see a need to keeping windows because I almost never play computer games. I saw this is the way to go and just wanted to hear if this would fix the problems with grub.

---

### Post by PMatt on 2007-05-17
bump one last time before I try this for better or worse!

---

### Post by adrian15 on 2007-05-18
> **PMatt said:**
> I was dual booting windows from the internal and ubuntu from the external.
Can you please confirm me that you once dual booted windows from the internal hard disk and that you could also boot ubuntu from the external hard disk?

That changes things a lot. It's not a problem of your BIOS recognising your drives but a problem from a bad menu.lst configuration or a bad grub installation on the external hard disk.

adrian15

---

