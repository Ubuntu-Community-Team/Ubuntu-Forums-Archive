---
title: "boot problem from CD"
date: 2005-07-14
forum: Apple PPC Users
---

### Post by omid455 on 2005-07-14
I have an imac G3 400 mhz slot loading machine whit osx.
I can not boot from ubuntu cd. when I format the disk and there is no mac os it is ok I can boot to linux from cd. but when there is mac os on the machine it does not boot from linux cd. only from mac os cd i can boot.

Thanks.

---

### Post by DJ_Max on 2005-07-14
I have the same exact iMac you have. How do you go about booting the CD. Do you hold down 'c'?

---

### Post by s.locke on 2005-07-16
I have a similar problem.  I will update this post when I've found a fix.

(Indigo iMac 500mhz/CD-R stalls when trying to selecting kubuntu 5.04 install CD in first stage bootstrap.  It returns me to the menu.  If I select CDROM again it freezes.)

Currently the machine has Debian 3.0r1a installed (not for long, if I can help it.)

Locke Murray

---

### Post by s.locke on 2005-07-17
I attempted install with a ubuntu 5.04 powerpc install CD.  Various installer options resulted in varying errors.  (power3 options cause kernel panic, generic ones fail with the characteristic red error screen at the "multiseat" configuration step.

I am unable to determine why these late-G3 iMacs  are having such a hard time.

S. Locke Murray

---

### Post by DJ_Max on 2005-07-17
My iMac G3 had no problem multiset configuration, in which 80% of people will never need. Power3 are for the orginal IBM Power3 computers, Apple uses modified Power computers. For example, the G5 is actually based on the Power4.

If your only problem was with the multiseat configuration, skip it.

---

### Post by PeteLM on 2005-07-18
Hi I have a G3 366 clamshell iBook and am experiencing the same porblems. Mac OS 10.3.8 is already installed, taking up the whole 10GB drive.

I downloaded thh Kubuntu ppc iso and burned it to CD using windows XP. I then inserted the CD in my iBook, rebooted the machine and held down the 'C' button, the CD made it's usual noises, but Panther booted instead. I tried this several times but to no avail, Panther kept booting.

I opened the Kubuntu iso CD in Finder, and the iso file had the hard disk icon so typical of a Mac OS X *.dmg file, but nothing happened when I clicked it. I also found a yaboot and yaboot.conf, both had the blank white page icon (meaning that Panther did not recognise the file type). When I clicked on the icon for yaboot, Panther stated that "the application used to create this file could not be found" and opens a browser for you to manually find a program to open the file, but I have no idea what program Panther would use. Simialry with the Power 3 files (assumed they were for G3) there was a SIT type of file that Stuffit Expander opened, but the resulting init file also had the blank page icon and Pantehr reported the same message about not being able to find the application used to create the file.

Have I done something wrong? Or do I need to take the brave step and blow away Panther before putting Kubuntu on? Also I understand I need to create 3 partitions ... yaboot (16MB), swap (2 x RAM) and / (root), is this corrrect?

Any Help Greatly Appreciated.
Cheers
Pete

---

### Post by DJ_Max on 2005-07-18
[QUOTE=PeteLM]Hi I have a G3 366 clamshell iBook and am experiencing the same porblems. Mac OS 10.3.8 is already installed, taking up the whole 10GB drive.

I downloaded thh Kubuntu ppc iso and burned it to CD using windows XP. I then inserted the CD in my iBook, rebooted the machine and held down the 'C' button, the CD made it's usual noises, but Panther booted instead. I tried this several times but to no avail, Panther kept booting.

I opened the Kubuntu iso CD in Finder, and the iso file had the hard disk icon so typical of a Mac OS X *.dmg file, but nothing happened when I clicked it. I also found a yaboot and yaboot.conf, both had the blank white page icon (meaning that Panther did not recognise the file type). When I clicked on the icon for yaboot, Panther stated that "the application used to create this file could not be found" and opens a browser for you to manually find a program to open the file, but I have no idea what program Panther would use. Simialry with the Power 3 files (assumed they were for G3) there was a SIT type of file that Stuffit Expander opened, but the resulting init file also had the blank page icon and Pantehr reported the same message about not being able to find the application used to create the file.

Have I done something wrong? Or do I need to take the brave step and blow away Panther before putting Kubuntu on? Also I understand I need to create 3 partitions ... yaboot (16MB), swap (2 x RAM) and / (root), is this corrrect?

Any Help Greatly Appreciated.
Cheers
Pete[/QUOTE]
 You did burn the cd as a Disk Image, right?

---

### Post by damonw5 on 2005-07-18
[QUOTE=DJ_Max]You did burn the cd as a Disk Image, right?[/QUOTE]
 You must use a program in Windows to burn the image, NOT the file:

[http://ubuntuforums.org/showthread.php?t=49293&highlight=iso+burn](http://ubuntuforums.org/showthread.php?t=49293&highlight=iso+burn)

---

### Post by PeteLM on 2005-07-18
Hi Damon
You've got me thinking. I merely used XP's facility to burn the iso image. There were no settings available to select things like finalizing disks, so I just assumed that since the file was an ISO image that this would automatically be made bootable. 

I also wonder if burning the CD on a PC instead of a mac is the problem. unfortunately, I don't have a phone line, so use Wintel boxes at an internet cafe. My PC at home has Nero, so should I just copy the ppc iso to the hard drive and then use Nero to burn a fresh CD, and look for a DIsk Image option?

I've been using various Linux distros on the PC since 1999, and whilst Kubuntu/Ubuntu have a few issues (as do all distros) it has such great potential to become the most popular distro. I also like the way Ubuntu and Kubuntu deliberately target non-Intel platforms.  As for my Linux/PPC experience I did once dual boot Yellow Dog 2.1 with Mac OS 9.0 on my old iMac. My clamshell only has 128MB RAM, running OS 10.3.8, so I know I need to get more RAM.

---

### Post by rdario on 2005-07-19
Trhouble: I have the same problem to boot from the UBUNTU CD,
Solution: 1.-Insert the UBUNTU install CD.
2.-Reboot, then press and hold down the Command (clooverleaf apple), option (alt), "o", and "f" until the system prompt
3.-type this:   boot cd:,\install\yaboot
4.-Wait until system prompt boot: type "install"

---

### Post by PeteLM on 2005-07-19
Thanks Damon You were spot on!
I used Nero to burn an 'iso disk' from the ppc iso image and the iBook booted into the Kubuntu installer!!!! I now have Kubuntu on my iBook!  :grin: 

The installation was quicker than when loading Panther and iLife by about an hour (2 hours total to Kubuntu logon), whereas Panther actually took 3 hours (add another 45 mins to load the developer tools).    

Kubuntu is a little slower than Mac OS 10.3.8, but I only have 128MB of RAM. Initially there were graphics glitches with some of the fonts and backgrounds, so I went into Control Centre -> Peripherals -> Display and Applied the existing settings so no more glitches. The first thing I notice was that KDE fonts were far sharper than Panther. Kubuntu found the sound system too! I'm that impressed I'm going to put Kubuntu on my G3, and set my G4 up to dual boot between Panther and Kubuntu.

Thanks again for all your help. I hope my update helps others having problems booting from the Install CD. Next job is to  max out the RAM to 576MB! :grin:

---

