---
title: "Guidelines on dual boot (Win7=SSD/Ubuntu=2ndHD) with ExpressGate button on Asus N53SM"
date: 2014-03-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by GordTheRogue on 2014-03-21
Hello everyone, I'm Gord The Rogue from Italy.
First of all mine situation:
Yesterday I started my laptop, an ASUS N53SM-S1096V, and got a S.M.A.R.T. warning error. I checked my HD and got 16 bad sectors (open write). So today I bought two brand new HDs, one Crucial M500 240Gb SSD and one Hitachi Travelstar 7k100 1Tb.
I know that maybe I can solve the errors with badblocks, but before that I need to backup everything, also I use the occasion to upgrade to SSD and a 2nd HD (with a caddy bay in DVDdrive). On the faulty HD I've Win7 installed with the recovery partition made by Asus.

**My goal:** To have a dual boot laptop by using the ExpressGate button for Ubuntu (installed on the 2nd HD Hitachi) and Power button for Win7 (installed on the SSD, mainly for gaming)

I've searched a lot and got too many confusing inputs about installing Win7 on the SSD and Ubuntu on the 2nd HD, so I'm here to have some guidelines by who made it successful.
For the ExpressGate button I'm referring to this thread, they talk about Grub4DOS: [http://ubuntuforums.org/showthread.php?t=1410167&page=2&p=10863855#post10863855](http://ubuntuforums.org/showthread.php?t=1410167&page=2&p=10863855#post10863855) (sadly closed)

What I can't understand is how to manage the bootloader and if I need to clone on the SSD the Asus's recovery partition. I'm going, cause as a Student I can, to download a LEGIT copy of Win7 from MS sites. 
**What are the full steps to get rid of this? ** 

My idea (simple steps) is to install Win7, install Ubuntu, install Grub4DOS to make the ExpressGate's button mod. Am I wrong? Please let me know your considerations, cheers!

---

### Post by GordTheRogue on 2014-04-03
Hello, after some tweaking I've got it run. For who's interested here are the steps I've done:

- Install MS Windows on the SSD.
- Download and run Ubuntu Live from a USB pen drive. (Change BIOS's boot sequence to boot from USB)
- Split the second HD (the one in the caddy bay in DVD drive) into some partitions, mine are in sequence: 10Gb (primary) /swap - 5Gb (primary) /root - 10Gb (logical) /usr - 250Gb (logical) /home - 5Gb (logical) /var - 1Gb (logical) /tmp - 670Gb (primary) NTFS for data.
- Download and run Ubuntu installation from a USB pen drive. _D_[FONT=verdana]_on't run the Ubuntu installer from Win!_ It will mess the MBR on the SSD, pay attention! _Boot from USB_.[/FONT]
- Install everything into the assigned partitions.
- **Install GRUB on the** /dev/sdb (in my case the **second HD** was sdb, check your with [FONT=courier new]cat /proc/partitions .[FONT=verdana] Don't install it on the MBR of the SSD.
- When Ubuntu's installation is finished restart the laptop, it will start Win without Grub menu.
- Follow the instructions from this topic: [/FONT][/FONT]http://ubuntuforums.org/showthread.php?t=1410167&page=2&p=10863855#post10863855 but pay attention to the [FONT=courier new][COLOR=#000000]root (hd0,2)[/COLOR][/FONT][COLOR=#000000][FONT=verdana].[/FONT][/COLOR][FONT=verdana] Mine was [FONT=courier new]root (hd1,2)
[FONT=verdana]- When finished, restart Win, there must still no presence of Grub menu. So turn off the laptop.
- Try to turn on the laptop from the ExpressGate button (top left key). It will boot with the Grub menu if everything is ok.
- Enjoy!

I hope this will be helpful for someone. [/FONT][/FONT][/FONT]

---

