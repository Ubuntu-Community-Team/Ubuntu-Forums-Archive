---
title: "Cannot Find Kernal Image"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by cureheal on 2006-11-08
i have a laptop that does not have an optical drive. So i tried installing Ubuntu from a usb key. 

I followed the instructions on the guide. But i get this error all the time no matter what i try.

"Could not find kernel image:"

There was no OS installed when i bought this laptop a few days ago.

Help me~~ I really need to use my laptop soon.

---

### Post by MasterOfDisaster on 2006-11-08
I got this error when my CD burnt incorrectly.  Try recopying the Ubuntu .iso onto your USB drive.

---

### Post by cureheal on 2006-11-08
I did it many times with different copies. I was wondering about the hidden files. I'm using a mac. DO you know if Mac hides files like Windows?

If it does, that might be why. Otherwise, i download Ubuntu more than 5 times and tried, but it never worked out.

---

### Post by blitzer on 2006-11-08
> **cureheal said:**
> i have a laptop that does not have an optical drive. So i tried installing Ubuntu from a usb key. 

I followed the instructions on the guide. But i get this error all the time no matter what i try.

"Could not find kernel image:"

There was no OS installed when i bought this laptop a few days ago.

Help me~~ I really need to use my laptop soon.


You didn't list the guide so I don't know what it told you.  You might try and check you bios on bootup: usually hit the F-1 key or Delete key check your manual on which it is - or read your bootup screen for which key it is.

If your bios supports bootup to usb then you need to select it to look to usb first then hard drive.

Good luck 8)

---

### Post by cureheal on 2006-11-08
I used the guide on the Ubuntu Website. I think i found it under "documentation"

I will post a link to it. 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

My laptop can boot on a USB drive. So i saw the Ubuntu icon at the top of my screen when my laptop booted 

up. And i get this the kernel image error message. 

I'm so clueless because the guide has no mention of the kernel.

---

### Post by blitzer on 2006-11-08
Sounds like the Flash drive in not setup correctly as a bootdisk.  The instructions that are posted were given from a windows machine how-to and you were setting up the Flash bootdisk from a mac ?   

I'm not an expert but this might be your problem.  
> 
Checking your USB stick

Booting from USB memory sticks is neat, but there is no guarantee that it works with your particular combination of computer and USB stick. Even if you are able to boot from your flash drive on one computer, this does not mean that it is going to work with the next one. You can try experimenting with different settings in your PC's BIOS to make it work.

Since you will want to fit all of the Ubuntu installation CD onto the flash drive, make sure to pick one that is large enough to hold the contents of the installation CD. Since you will use SYSLINUX to make the flash drive bootable, make sure that it is formatted with a FAT16 filesystem. (SYSLINUX does not support booting from partitions formatted with the FAT32 filesystem according to the SYSLINUX documentation.) Luckily most USB flash drives come formatted with a FAT16 filesystem to begin with, so there is probably nothing to work about. A flash drive with 1 GB capacity would be perfect. :-)
Making your flash drive bootable with SYSLINUX

SYSLINUX is a boot loader that operates off an MS-DOS/Windows FAT filesystem. Most USB flash drives come with a FAT filesystem. Here's how you can add a SYSLINUX bootblock to your USB stick:

---

### Post by cureheal on 2006-11-08
WoW. You read the guide?? Thank you very much for your time and efforts to figure out my problem. 

Syslinux can only be run on Windows. So i used parallels to do all the stuff that the guide instructed me to 

do.

I formatted my usb drive on Windows, ran sislinux on Windows. But only thing that i did on Mac was copying 

the contents of the cd into my USB drive.

I don't know if mac hides files like Windows because the file that the guide says is hidden on Windows was 

not hidden on Mac.

USB booting is fine. I tried the HP usb Utility thing and made my usb work like a booting disk. I got Dos working on my USB. It worked fine 

except i could not run Setup.exe file on the cd because "it was not the windows setting." that was the error 

message.

I thought that the problem might come from having no OS installed. But i'm not sure. 

I hope you get the whole picture now. Thanks again for your time and effort.

---

### Post by blitzer on 2006-11-08
:-D  No problem.

> I formatted my usb drive on Windows, ran sislinux on Windows. But only thing that i did on Mac was copying

the contents of the cd into my USB drive.  [COLOR="Red"]I think this is the problem but I have NEVER used a Mac ](*,) [/COLOR]

I don't know if mac hides files like Windows because the file that the guide says is hidden on Windows was

not hidden on Mac.


> I got Dos working on my USB. It worked fine

except i could not run Setup.exe file on the cd because "it was not the windows setting." that was the error message.  [COLOR="Red"] *Not sure* but should be install and not setup :-k [/COLOR]

I thought that the problem might come from having no OS installed. But i'm not sure.  [COLOR="Red"]The bootup disk or flash drive is a temp OS untill install like I said I'm not an expert.  Maybe someone else might be reading and help you out ;)[/COLOR]

---

