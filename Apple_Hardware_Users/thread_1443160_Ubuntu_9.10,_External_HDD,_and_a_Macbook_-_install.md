---
title: "Ubuntu 9.10, External HDD, and a Macbook - installation issues"
date: 2010-03-30
forum: Apple Hardware Users
---

### Post by BUKiT on 2010-03-30
Let me begin this post by saying that I am completely new to Ubuntu.  

I recently downloaded 9.10 and attempted to install it to an existing 35 GB partition on an external hard drive using my Macbook.  I did this by shutting down my computer, plugging in the external drive, and booting from a CD to which I had copied the .iso file.  I selected my desired language and chose to install Ubuntu.  After manually selecting the desired partition, I resized it to 25 GB, formatted it to ext4, and mounted it as "/".  I then used the remaining free space to form an additional partition of 8 GB (double my RAM) for use as "swap space."  The rest of the installation steps were uneventful, and I restarted my computer at the end of the installation.  

I also have Mac OSX installed one of the external HDD's other partitions, and the computer booted straight into that partition when restarted.  After shutting the system down again and booting using the "option" key, the computer only gave me the option of booting into the Mac OSX partition on my external drive - the Ubuntu partition and my internal hard drive were conspicuously absent.  

I have since tried shutting down the computer and booting without the external HDD plugged in, and all I get is the grey screen with a flashing folder/question mark icon.  With the external drive plugged in, I can still boot from the Mac OSX partition and access the contents of my internal hard drive, which appear completely intact.  

Not sure what the problem is here, but I would like to be able to boot into OSX from my internal drive and would also appreciate any tips for installing Ubuntu on the external partition if possible.

Any advice is greatly appreciated.  Thanks.

---

### Post by ubunterooster on 2010-03-30
Is this an Intel&#8482; CPU macbook? If so use the regular 64bit version of Ubuntu (unless you use a 32bit CPU) 

Is this an Apple&#8482; CPU? If so, you will need the PPC version.

---

### Post by BUKiT on 2010-03-30
Forgot to include that.  I normally run Mac OSX 10.6.4 on a 2.4 GHz Intel Core 2 Duo black macbook with 4 GB 677 MHz DDR2 SDRAM.

---

### Post by ubunterooster on 2010-03-30
To properly burn a .iso image:

Load the disc utility (found in the Utilities) 
Insert a blank cd 
Choose: Images>Burn and select the .iso file.


Merely copying the .iso to cd will not work.

---

### Post by BUKiT on 2010-03-30
I'm not sure that this is a 32 vs. 64 bit issue.

Either version (I've tried both) seems to install to the external HDD just fine.  It seems that once I restart the Macbook to complete the installation, I am unable to access either the Ubuntu partition on my external drive or my entire internal hard drive.  Only my Mac OSX external HDD partition is accessible.  Furthermore, with the drive unplugged, the computer won't boot into the internal hard drive, it only shows the grey screen with the flashing folder/question mark icon.  And yet the internal drive is completely intact, because I am able to access its contents when booting OSX from the external drive.

I appreciated your help.

---

### Post by ubunterooster on 2010-03-30
GRUB issue. :(

I think you need the alternate disc. It will allow you to specify where to stick grub. Most likely it is installing GRUB on the external drive (overwritting the MBR on your main drive), so you want to specify your main drive for the GRUB location.

Sorry, I was not paying complete attention before.

---

### Post by srs5694 on 2010-03-30
Macintoshes are EFI-based, not BIOS-based, which means that MBR-based bootloaders are irrelevant. EFI-based systems ignore the MBR-based boot code found on BIOS-based computers. Although there is an EFI-enabled GRUB 2 variant, I have no idea if Ubuntu attempts to install it on Macs.

I recommend you post in the [Apple User's](http://ubuntuforums.org/forumdisplay.php?f=328) forum, since your problem is one related to booting Apple's variety of EFI, and most people here in the "General Help" forum use BIOS-based computers and won't be able to offer much useful advice. Of course, somebody might happen by with the knowledge, but this *is* an Apple/EFI-specific problem.

---

### Post by Joeb454 on 2010-03-31
Thread moved to Apple Users forum :)

---

### Post by linuxopjemac on 2010-03-31
I would start by booting into the OSX partition and install the newest version of rEFIt (0.14), downloadable [here]("http://refit.sourceforge.net/#download"). Then from within rEFIt, you sync the partition table. Then you try to boot into Linux.

---

### Post by BUKiT on 2010-03-31
Wow, rEFIt worked wonders.  After running the partition syncer, I now have my internal hard drive available.  First problem solved.  

But when I boot with the option key, I get three choices - booting OSX from the internal hard drive, booting Ubuntu from the internal hard drive, and booting into rEFIt to access the external drive.  When I choose to boot into Ubuntu from the internal hard drive, i just get a black screen that says "GRUB," and a flashing cursor in the upper corner.  Booting into the external drive takes me to the rEFIt menu, where I can boot into either external drive installation of OSX or a copy of the OSX install disk that I also have on the drive.  The 25GB partition with 8GB swap space on which I have Ubuntu 9.10 installed is unavailable.  All of which leads me to believe that I have somehow installed the GRUB bootloader on my internal hard drive when it should be on the external drive with the rest of the Ubuntu OS.  

Am I thinking about this correctly?  Is there a way to remedy this issue?

---

### Post by linuxopjemac on 2010-03-31
You have to start from a liveCD and chroot into your system. Then grub-update, or grub-install on the desired drive (/dev/sdb for example, if that is your external drive).

[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

