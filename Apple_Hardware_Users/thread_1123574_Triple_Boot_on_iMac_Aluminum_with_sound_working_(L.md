---
title: "Triple Boot on iMac Aluminum with sound working (Leopard, Windows, Ubuntu)"
date: 2009-04-12
forum: Apple Hardware Users
---

### Post by Booboo85 on 2009-04-12
This is for people who want to enjoy Ubuntu either secondary or tertiary to Mac Leopard or Windows X on Mac, because this method limits the Ubuntu OS to 30GB storage space. This method requires Windows X.

Method Outline:

This method is a configuration the iMac's compatible with, allowing you to avoid the infamous and immortal 'Linux Swap File', if one day you wish to reclaim your HD from Windows and Ubuntu altogether, without reformatting your Mac HD. This method works with Mac OS X Leopard's design and it is safe.

What I have:

24-inch 
2.66GHz Intel Core 2 Duo
4GB memory
640GB hard drive1  	
8x double-layer SuperDrive
NVIDIA GeForce 9400M graphics

Mac OS X Leopard
Windows Vista Ultimate
Ubuntu 8.10

What NOT to do:

*Do not use Ubuntu 8.04
*Do not update manager Ubuntu 8.10 my instructions indicate in Part B.

What to do (general):

**Part A (Boot Camping Windows, Installing Ubuntu)**
1. Have Mac OS X Leopard updated and running smoothly.
2. Install Windows X with boot camp, which is located in Applications/Utilities.
3. In boot camp, partition perhaps 160GB for Windows X.
4. After reboot, eventually reach drives screen, choose BOOTCAMP hard drive, choose Format, which makes it NTFS. 
5. Install Windows X and reboot into Window X an login. 
6. Install windows support from Leopard Mac OS X DVD, before updating Windows X. Update Windows X and restart Windows X as updates indicate.
7. Get Windows X updated and running smoothly. 
8. Burn Ubuntu 8.10 to CD. Insert Ubuntu CD and choose 'Install Ubuntu INSIDE Windows'. Choose the maximum space of 30GB for Ubuntu. *Make a Password for Ubuntu.*
5. Remove Ubuntu CD when it slides out the iMac and Reboot as Ubuntu completed installation prompt indicates. 
6. Select Ubuntu from boot options and logon to Ubuntu.

Logged inside Ubuntu you now have 1280X940 video resolution, which we will fix in part C. You have no sound, which we will fix in part B.

**Part B (Get your Sound Working)**
1. From the panel, Choose Applications/Accessories/Terminal.
2. Enter: sudo gedit /etc/modprobe.d/alsa-base and when alsa-base text file opens, as a last command at the end of alsa-base file, enter: options snd_hda_intel model=mbp3 and now save and close.
3. Back to terminal, enter: sudo gedit /etc/modprobe.d/options and when options text file opens, as a last command at the end of the file, enter: options snd_hda_intel model=mbp3 and now save and close. Close Terminal and Reboot back into Ubuntu.

**Part C (Beautify your Screen Resolution)**
1. Get your internet connection working by System/Network Configuration, Wireless(?), +Add, enter your router settings. 

*YOU MUST HAVE INTERNET TO PROCEED*

2. From the panel, Choose System/Administration/Update Manager and get your system updated installing all that's checked and restart once manager is finished and boot back into Ubuntu.


*YOU MUST HAVE INTERNET or this will fail/will not 'Activate'.*

3. Back in Ubuntu, from the panel, Choose System/Administration/Hardware Drivers and allow scan and after scan finishes choose only and exactly 'NVIDIA accelerated graphics driver (VERSION 180) [Recommended]'

*Do not choose (version 173)*
*Do not choose (version 177)*
*DO NOT CHOOSE BROADCOM STA WIRELESS DRIVER*

4. Activate the correct graphics driver. Close window. Restart Ubuntu, booting back into Ubuntu.

**Part D (Finishing up)**
1. Now logged back into Ubuntu, adjust your screen resolution in System/Preferences/Screen Resolution through panel. Plug your speakers into 'HEADPHONE' output on the right-side back of your iMac for sound. Perform a sound test.

***You can boot up Windows X without needing to log into Leopard. During any restart cycle of your Mac, press and hold down the Option/Alt key on your keyboard, during the 'white screen' phase of your Mac boot. Holding Option soon displays your Macintosh HD and your Windows X Hard Drive as high-graphics icons on your white screen. Use your mouse to choose either Macintosh HD or Windows X. Choose Windows X to get to Ubuntu. During the DOS boot sequence after choosing Windows, you will have 7 seconds to choose between Windows or Ubuntu. This is the traditional DOS dual-boot method. Choose Ubuntu and you're good to go!***

To fix your Windows partition from showing up as 'Untitled' on your Leopard Desktop, when logged into Windows go to My Computer and change the name of 'Local Disk' to Windows Vista or whichever name you like. This will not hurt anything. It is OK to do.

*VERY, VERY IMPORTANT*
Do the following or your triple booting has a degrading effect on Leopard's applications. If you do not do this, you may first notice iTunes in leopard is forever frozen, remedied only by Force Quit. Next Safari will eventually start doing the same. This is your disk integrity failing. Running Disk Utility while Leopard is still running and the Macintosh HD mounted is not effective. Your Disk Utility will say 'appears to be OK', but it is wrong. Follow the instruction below and finally you're home free to enjoy your triple booting...

Once you eventually get back logged on Leopard, insert your Mac OS X Install CD, click Install Mac OS X and restart your Mac as the dialogue window will indicate.
Once booted up by the Mac OS X CD, look up to the panel at the top of your screen, click on 'UTILITIES', scroll down to Disk Utility. In DISK UTILITY, in the First Aid section, click on your Macintosh HD and still in First Aid, click on REPAIR DISK. This takes only 1 minute. Once Repair Disk is finished, close Disk Utility, go back up to the panel at the top of the screen and click on Mac OS X Installer/Quit Installer.  The start up option will appear.  Choose 'Macintosh HD'. This was necessary because Disk Utility must be run when your HD is unmounted and that is why we started up through the Mac OS Install CD, instead of just running Disk Utility from inside Leopard. What we have done is some housecleaning, restoring your disk to optimal health after your triple booting process.

You're good to go and all fixed up. Everything functions beautifully now. 
Enjoy!! 

Special Thanks: ):P

Kimmik from Germany on ubuntuforums.org/showthread.php?t=831314
(provided very simple non-patch sound usage in Ubuntu on iMac)

Mara Sorella of answers.launchpad.net/ubuntu/+question/20998
(provided sudo gedit command and alsa-base, options location)

---

