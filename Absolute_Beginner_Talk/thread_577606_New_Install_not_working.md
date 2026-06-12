---
title: "New Install not working"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Jezprice on 2007-10-16
I have just installed Ubuntu - latest fiesty - onto my computer and can not get it to install?

I have XP on one partition a data storage partition and ubuntu on the 3rd (i guess swap is a 4th?). 

XP and data partitions were installed prior to ubuntu, then i set up a partition for Ubuntu and a swap partition - followed from instructions off this forum. 

It installed fine and restarted, showed up Ubuntu, ubuntu recovery, memory check and XP in the list of OS to choose from but when i select Ubuntu it gets to the logo screen and 1 block of the status bar goes orange....................thats it?

XP works fine as before.

Any help will be gratefully welcomed.

p.s. this is my first ever install of Ubuntu/linux and i am as green as grass!

---

### Post by overdrank on 2007-10-16
> **Jezprice said:**
> I have just installed Ubuntu - latest fiesty - onto my computer and can not get it to install?

I have XP on one partition a data storage partition and ubuntu on the 3rd (i guess swap is a 4th?). 

XP and data partitions were installed prior to ubuntu, then i set up a partition for Ubuntu and a swap partition - followed from instructions off this forum. 

It installed fine and restarted, showed up Ubuntu, ubuntu recovery, memory check and XP in the list of OS to choose from but when i select Ubuntu it gets to the logo screen and 1 block of the status bar goes orange....................thats it?

XP works fine as before.

Any help will be gratefully welcomed.

p.s. this is my first ever install of Ubuntu/linux and i am as green as grass!

Hi and welcome, I take it that you ran the live cd fine? If you could give us some specs on your system? that would help us.

---

### Post by Jezprice on 2007-10-16
Hi

Live CD worked fine and i had been using it for a couple of weeks to get the feel for Ubuntu.

System is SG33g5 shuttle barebone
C2D 6550 - not overclocked - 1333fsb
2GB OCZ 800mhz  
500GB hard drive (80gb XP, 40gb Ubuntu - 2GB swap, rest storage for data an another partition)
DVD R/RW

Hope this helps?

---

### Post by overdrank on 2007-10-16
> **Jezprice said:**
> Hi

Live CD worked fine and i had been using it for a couple of weeks to get the feel for Ubuntu.

System is SG33g5 shuttle barebone
C2D 6550 - not overclocked - 1333fsb
2GB OCZ 800mhz  
500GB hard drive (80gb XP, 40gb Ubuntu - 2GB swap, rest storage for data an another partition)
DVD R/RW

Hope this helps?

Hi and I apologize  what type and model of graphics card ?

---

### Post by Jezprice on 2007-10-16
Its the onboard graphics that come with the shuttle Intel G33 + ICH9DH.

[http://hq1.shuttle.com/products_page03-spec.jsp?PLLI=551&PI=635](http://hq1.shuttle.com/products_page03-spec.jsp?PLLI=551&PI=635)

I am using the hdmi output to a dvi connector on my dell 2007wfp monitor and i have had no issues with graphice ever on my system.

---

### Post by twiceasworn on 2007-10-16
Well it sounds like Ubuntu is enocuntering a rather serious error on boot.  I would suggest booting into recovery mode to see if you are able to get it to boot that way.  It very well may be an issue with the integrated graphics but im not sure.  Also, when ubuntu is trying to boot and is at the splash screen try pressing alt-f1 or alt-f2 and see if you can bring up a tty.  This will show you what is going on at start up, and it will be very easy to see if something is wrong and what that something is.

---

### Post by Jezprice on 2007-10-16
I have tried booting into recovery and i get to an myusername@desktop or something like that (text) and if i push enter it repeates this line - my user name@..... until i restart the machine.

I cant see it being the graphics as it all works with the live CD?

How do i do a re install of ubuntu - though it installed okay last time as far as following the steps goes?

---

### Post by Jezprice on 2007-10-16
Whats the splash screen and a tty? I ask so i know when to push alt+f1 as mentioned.

---

### Post by Jezprice on 2007-10-17
Okay I have put the live CD back in and re booted, i selected to start with safe graphics from the list incase my graphics is the problem.

This is the error message i get

/bin/sh: cant access tty job control turned off
(initramfs) [34.370075] ata 3.00: failed to set xfermode (err_mash=0x44)

Does this make sense to anyone?

I really dont want to be put off ubuntu this early on in my learning!

---

### Post by PlantHead on 2007-10-18
I have the same shuttle SG33G5 working with feisty. Took me a while to get it going but its working great now.

boot using the livecd.
Select configuration from the menu at the bottom, its f6 I think.

If you have UBUNTU installed select the boot from harddisk and add IRQPOLL.
If you are installing for the first time, selct install and add /IRQPOLL to the end of the line eg. ro quiet splash /irqpoll

when you get ubuntu to boot you can add IRQPOLL to /BOOT/GRUB/menu.lst 
ie
open that file up, scroll down to you see the load kernel lines and add IRQPOLL
kernel	/boot/vmlinuz-2.6.20-16-generic root=UUID=ea52dbed-6d67-4ac3-b971-dee3234c0abb ro quiet splash IRQPOLL

I you are using the HDMI port don't to begin with. Get it up and running and sort out your GFX card driver, then switch back to HDMI.
I still get the occasional freeze on boot, just reset and start again.

---

### Post by PlantHead on 2007-10-18
[http://ubuntuforums.org/showthread.php?t=494943&highlight=g33](http://ubuntuforums.org/showthread.php?t=494943&highlight=g33)

have a look there to get your intel GFX working.

---

### Post by luis.alves@lafaspot.com on 2007-12-16
Hi

I also have a sg33g5.
Q6600 Quad core
2 SATA seagate 750Gb
1 DVD burner memorex
2 2Gb DDR2 Corsair


1 - Booting after install:

I found some problems with gutsy, installed from the CD on the first boot
it did not boot from the HDs

Bios in IDE mode did not boot from HDs but booted fine from the CD drive.
I changed it to ACHI, and it worked fine.

2 - USB DVI switcher makes gutsy stop booting process.
I have a DVI monitor switch for 4 computers with USB/mouse/sound switching  support.
Gutsy does not boot if the USB cable is connected, it gets stuck. I removed the USB cable from the DVI switcher, Plug in just a USB keyboard to the box booted again, and gutsy starts fine. After gutsy is started I plug the DVI switcher and it works just fine.

3 - Gutsy 32bit can only see 3.5Gb of memory. This is related with 32 bit limitations.
     Fix: I installed the 64 it's version and all is fine. 
     flash will give you some pain to get it working on gutsy 64 bit. S I used this script:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

4 - Dual screen monitor required me to run xrandr and add this to xorg.conf file
Section "Screen"
	SubSection "Display"
>>		Virtual  2048 2048

this command enabled Dual monitor support:
xrandr --output VGA --mode 1920x1200 --pos 0x0 --output TMDS-1  --mode 1280x720 --pos 0x1200

helpfull link:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Issues I still have are:

- Have the HDMI port detect my HDTV native resolution
- Have sound output thru the HDMI cable directly to the TV.

---

