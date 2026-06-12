---
title: "Trouble booting the Ubuntu install CD"
date: 2012-01-12
forum: Apple Hardware Users
---

### Post by INVICTUSHB on 2012-01-12
[CENTER]First off i would like to just say sorry if this has already been discussed. I've tried a couple of different Google searches so could just be a possibility i'm not finding anything because of my word choices.[/CENTER]

So i recently purchased a brand new Macbook pro about a month ago. I have windows 7 dual booted through bootcamp. I have installed ubuntu on a couple of my PC's by wubi and USB but have never installed through CD. Okay so I decided to triple boot with Mac, Windows 7, and Ubuntu. I burned the Ubuntu CD just like the site said through disk utility. Restarted my machine and held C and this the CD Drives makes a bunch of noise as if its reading the disk then boots Windows 7.

Anyone know what I am doing wrong? Thank you in advance to everyone that tries to help me solve this problem. Even if its something so simple maybe it will help other people too.

---

### Post by imachavel on 2012-01-12
it's not clear you are doing anything wrong. Computers are some times retarded. It should work, does it say the install finished before you restart the computer? It is often better to partition the drive before you install even on OS, but if you bought the laptop with windows then I can understand not wanting to reinstall everything if it's a pain. 

Are you sure you are installing the OS and not just booting to the live cd? You said you did it correctly though. Also you said you can dual boot mac and windows, so you can choose either mac or windows through the grub? But if you choose linux through the grub then it boots up windows instead? I would try downloading the boot repair disk and running it to see if it fixes grub issues. Of course I'm always cautious when it comes to windows grub and master boot record, ms dos based file systems don't like being changed. Sorry that this is how OSes typically work, the more popular one for some reason is the least stable, but at the same time the most universal :confused:

---

### Post by imachavel on 2012-01-12
ok sorry I see what you are saying. It acts as though it is going to read the disk, then just boots windows 7. why did you get the idea to hold c? mac mobo bios works this way? Well I never heard of holding c, it should give you an option to choose the boot device. hold f2 or f12 instead and look for a boot option. Sorry I know nothing of mac main boards in laptops. However, it should all be intel based now. But then that doesn't necessarily mean the firmware or bios chip will be made by intel but I'm somewhat sure it is.

---

### Post by Linforcer on 2012-01-14
imachavel, this has little to do with the "motherboard"  but rather the firmware and the efi.
Indeed the default way to boot a mac off a cd is to press the "C" key during bootup.
Alternatively one presses the Option key (most of the rest of the world calls this Alt) to boot other Operating systems.


INVICTUSHB: I've encountereds this problem myself and I believe it has something to do with MBR vs. GPT issues.

I advice you to install rEFIt, if you have not already (which uses a so-called hybrid MBR) if only temporarily and see what the results are when you boot from CD from the rEFIt menu, though I should advise you that the current version of libparted (also the one used in the installer) will mess up your hMBR, and you will have to go into Mac OS and use the gpt disk tool  to rebuild the table, which is a lot of hassle.

I have just succesfully completed a triple boot install on both a MacBook and a Mac Mini and it is no fun matter.

i will try to explain what I THINK is happening.

Right now there are two partition tables on your hard disk.
GPT (GUID partition table), the type typically used by Macs
a fake MBR (Master Boot Record)

The later of these two is included to keep other operating systems from messing with the GPT.
The loader on the cd, because of an inconsistency, between these two, gets the partition wrong and boots from whatever partition you have windows on now.

When I did my install on the MacBook, I could boot from the cd no problem, but I do not remember if I did it from rEFIt or not, and on the mac mini I had to first dd the install disk to a partition on the hard disk and install from there, and indeed it did try to run windows. So I made sure I temporarily changed the hybrid MBR to make the 4th entry the partition I was looking to boot.

Finally if you do succeed, you will have to follow the instructions in the top part of the post [here]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185").

I realize this may all be very confusing and not helpful. I had to do a lot of reading and learning about EFI, GPT and all that before I could understand all this stuff... 

I suggest you start at [this guide]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac_OSX.2C_Vista.2C_and_Ubuntu"), and see what problems you encounter. (It's a guide for triple booting OSX, Vista, Ubuntu but that shouldnt change for W7)

---

