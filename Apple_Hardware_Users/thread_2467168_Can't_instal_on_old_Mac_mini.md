---
title: "Can't instal on old Mac mini"
date: 2021-09-17
forum: Apple Hardware Users
---

### Post by fozzie103 on 2021-09-17
I have recently come across in the back of a cupboard a Mac mini circa 2007 stuck in the world of OsX leopard. A long time ago I managed a major project based on Sunos which was a Berkley Unix derivative so I thought I would try installing Linux and get some use out of the old box.
Then discovered my grandson, about to start a CyberCypto degree at warwick who could make use of a Linux standalone.
Following what I found on the net I downloaded Etcher and installed it on my MacBook.
I then downloaded ubuntu-21.04-desktop-amd64 and used it with Etcher to build bootable USD.  The Mac didn't recognise it as a bootable source when I started the startup manager.
Had a brainwave "the machine may be only 32 bit and the bistro is probably 64 so tried again with an olde version, used 15.04, still no joy.
Next step was to put the .iso on a dvd, then start the Mac booting from the DVD drive, this worked until it came up with choose which installation 1 or 2.
The only keyboard I have is bluetooth, although I did try one with a USB plug but nether produced any reaction.
Where do I go form here
HELP please

---

### Post by grahammechanical on 2021-09-17
Hardware specification would be useful. Did the mouse not work either? Just to be clear, what version of Ubuntu are you trying? Ubuntu 21.04 or 15.04? If I read your post correctly, Ubuntu loads from the DVD disc until you get to the Try or Install screen? And there is no response from the keyboard?

Do you need to enter the BIOS/UEFI settings utility to enable the keyboard? Is the keyboard recognised in the BIOS/UEFI settings utility?

Regards

---

### Post by fozzie103 on 2021-09-18
Hardware spec is
[FONT=&amp]Model Name:[/FONT][FONT=&amp]    [/FONT][FONT=&amp]Mac mini[/FONT][FONT=&amp]  Model Identifier:    Macmini2,1[/FONT]
[FONT=&amp]  Processor Name:    Intel Core 2 Duo[/FONT]
[FONT=&amp]  Processor Speed:    2 GHz[/FONT]
[FONT=&amp]  Number Of Processors:    1[/FONT]
[FONT=&amp]  Total Number Of Cores:    2[/FONT]
[FONT=&amp]  L2 Cache:    4 MB[/FONT]
[FONT=&amp]  Memory:    1 GB[/FONT]
[FONT=&amp]  Bus Speed:    667 MHz[/FONT]
[FONT=&amp]  Boot ROM Version:    MM21.009A.B00[/FONT]
[FONT=&amp]  SMC Version (system):    1.19f2[/FONT]
[FONT=&amp]  Serial Number (system):    YM83109AYL2

I was originally trying 21.04 then thought of possible problem re 64 or 32 bit so tried 15.04.

no: it doesn't load correctly from DVD, the machine appears to load but it stops at a totally black screen with a very faint load 1. or 2. and a data entry point. It doesn't reach the try or install screen.
bluetooth keyboard doesn't do anything neither did a USB connected keyboard. A usb mouse does nothing either.
Don't really know what you mean by BIOS/UEFI settings utility, the machine is currently running OS x Leopard which is all Macpseak

Hope this helps[/FONT]

---

### Post by grahammechanical on 2021-09-18
I use an Intel core 2 Duo. Ubuntu will run with 1GB RAM. I have done it. A lot will depend on the amount of memory in the graphic adapter. My machine now has 4GB RAM and a graphic adapter with 1GB of its own memory. It makes a big difference.

Ubuntu uses the Gnome 3 desktop environment and the Gnome 3 shell user interface. There are other desktop environments that use less memory. Xubuntu and Lubuntu are built on Ubuntu but the desktop environments use less memory than Ubuntu does. You might need to consider that.

Every computer motherboard has an integrated circuit (memory chip) that stores information about the computer as to what CPU it has, how much memory. That sort of thing. In the old days it was called Basic Input Output System (BIOS). In modern machines the method has been changed to something called Universal Extensible Firmware Interface (UEFI).

When my machine starts to boot I see a message on the screen saying "to enter BIOS press del." Maybe your machine gives the same sort of message. In this settings utility we set the date and time and can make other changes such as where the machine looks for an operating system. A hard drive? A DVD drive? Or a USB memory stick.

Please read the information on this link under Ubuntu CD Advanced Welcome Page Options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you can get to the screen with the icons of a keyboard and a human, then press any key. At the next screen press F6 other options and when the menu appears select nomodeset. We press ESC to leave the pop up menu. Then we can select Try Ubuntu.

To do all that we need to have a working keyboard. Which is why I am talking about the BIOS/UEFI settings.

Regards

---

### Post by coconutdog2 on 2022-06-14
A great resource to find all Mac specs. Just enter your serial number:

[https://everymac.com/ultimate-mac-lookup/](https://everymac.com/ultimate-mac-lookup/)

---

### Post by kencu on 2022-09-21
I run Ubuntu on a machine like this. I put 4GB of memory in it, but it can only use 3.3GB. Otherwise it works pretty well for many things, email. web browsing with Chrome or Firefox, running Spotify, codeblocks, etc. Most things really. It just falls down on 3D graphics.

Because it has a 32 bit EFI, but you want 64 bit Ubuntu, you need to make a small mod to the boot DVD before you burn it. My alterations of the program needed to do that are here:

[https://github.com/kencu/Boot-64bit-linux-on-32bit-EFI-Macs](https://github.com/kencu/Boot-64bit-linux-on-32bit-EFI-Macs)

---

### Post by csae2608 on 2022-10-28
had trouble installing Ubuntu on such a machine for long time;
did install from DVD, external DVD-Burner;
whereas Debian Squeeze, Wheezy would install well, Ubuntu/Lubuntu the likes had more problems with DVD;
if you use Refit/Refind, you should be able to succeed easily. Good Luck!

---

### Post by xleggs on 2022-12-07
I'm trying the exact thing and getting the exact result. Did you make this work?

[https://ubuntuforums.org/showthread.php?t=2481700](https://ubuntuforums.org/showthread.php?t=2481700)

---

