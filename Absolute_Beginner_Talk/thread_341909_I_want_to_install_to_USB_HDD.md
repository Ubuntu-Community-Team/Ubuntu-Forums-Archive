---
title: "I want to install to USB HDD"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by hoarsecourser on 2007-01-19
I'm looking for help installing to a USB HDD (40G).  I have a laptop with a bunk optical drive (detected by XP but won't read any discs) and an old klunker that I can get Knoppix running on.  My laptop will boot from USB HDD quite happily, if it can find initrd...but I don't know how to get it to go.  How do I install a more linux-happy bootloader (without scaring XP away)?  Can I do it with the Edgy .iso file and Virtual Clone Drive? Thanks

---

### Post by OldTimeTech on 2007-01-19
This is something I found after doing a search through the forums on your problem, I hope this helps!


"One big issue I can see is if you install the grub bootloader to the MBR of your XP drive
you have 1) altered your XP install. 2) you will need to probably need to have your external drive connected every time you boot up.

Let me explain. If you allow the installer to place grub on the MBR of your main drive it will overwrite the XP MBR with what is called Stage 1 grub. Grub is the GRand Unified Bootloader. Stage 1 grub is a small file that points to a file on your Ubuntu Edgy drive called /boot/grub/menu.lst this file is located at the root (/) of your Ubuntu install.
It contains the info needed to boot Ubuntu (by default) and will boot Ubuntu or XP if the correct entries are there. You will be presented with a menu when you start your computer. If you drive is not plugged in when you start up stage 1 will point to a drive that
doesn't exist and you will get a grub error and no menu.

You can specify that grub stage 1 is installed to the MBR of your external drive.
This leaves your XP MBR alone.

However your computer BIOS needs to be able to boot USB external drives.
Most newer computers are able to do this.

My laptop for instance has a feature where if you press F12 during POST it will display a menu showing all the drives connected to my computer.

see below for install info

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and see this great tutorial about dual booting (this is a large tutorial) but you really
should read before doing anything.

http://users.bigpond.net.au/hermanzone/index.htm"

---

### Post by hoarsecourser on 2007-01-19
Thanks for the info.  My query is slightly different, I don't want to do a dual boot on my existing laptop hard drive...I want to install to an external hard drive.  When I take the HD out of my (now dead) other laptop (on which I had Ubuntu running happily, until I took it apart to do a RAM upgrade and now not even the BIOS will load) and attach it via USB and select it to boot (using F12, not unlike your computer) it begins an Ubuntu boot...but then bungles up at some point in the progress bar screen.  I'm wondering if there's a way to get the basics onto this external hard drive so it will boot, then I can download and configure the components as needed WITHOUT touching my existing XP HD.  Can I do it with Knoppix (only can get the shell running)? (e.g. format and partition the external HD, add initrd.gz and vmlinuz to the appropriate partition [don't know which that would be] then attach the prepped USB HDD to the destination machine to boot and configure)  Thanks again so much for your help!

---

