---
title: "install ok but continuous reboot"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-01-30
My computer continuously restarts when trying to boot.  I'm new, so I will try to explain as best as I can, but I don't know all the grub/kernel/etc lingo correctly.

I attempted to install 7.10 on a computer.  I was booting from LiveCD and everything would load fine.  As soon as the desktop appeared and everything seemed fine, I would go to install and the system would restart itself.  Sometimes it would restart before the desktop even loaded.

I installed the hard drive on another system and installed 7.10 from the same LiveCD, totally reformatted the drive and did a clean install.  I downloaded and installed all the updates while attached to that other system.  It boots fine attached to that other box.

I reconnected the hard drive to the original computer and it continues to restart before everything is loaded.
The system turns on and I can get into BIOS fine.  I don't think its a motherboard or overheating issue because I can leave it in BIOS for a long time.  Its not a power source issue, I checked that.  It loads and says "grub loading in...3...2...1..." and begins to load, the screen flickers and gives some weird lines, then restarts with the system memory test and detecting IDE drives again.

I disconnected all unnecessary peripherals, its just the MB, HD, Ethernet card and RAM. No floppy or CD.

I do not know how to change things or get different screens in the boot sequence, so any help will be great.  Thanks.

---

### Post by rubbsdecvik on 2008-01-30
Well, I have to thank you for the detailed description of what you did.  That helps a lot.  

My guess is that something may have been wrong with the LiveCD you had.  Sometimes they can become corrupted during the burn process.

We can try a few things.  One is that you can download a new LiveCD and try installing on that.  It's probably the easiest, but might not always take care of the problem.

You could also try to boot up in "RecoveryMode."  To do this reboot and when the "Grub Loading 3... 2... 1..." shows up hit "Esc"  That will get you into the GRUB menu.  The first line is the regular "ubuntu" OS.  The second is the "Recovery Mode" one.  Select that one.  It will get you into a commandline.  If you can get into that without it rebooting let us know... there might be something going on that we can help you fix.

---

### Post by TJCIB on 2008-01-30
I do not think it is the LiveCD.  I have installed onto other computers using the same CD since then with no problems.

I can get to the grub menu with regular, recovery, and memtest.

When I hooked up the CD Drive to try to boot with a LiveCD, I don't get the normal install screen.  I get the other one that gives me the "boot:" prompt.  I tried booting in safe mode with no luck.

Thanks for the help.  I'm very curious as to what it might be.

---

