---
title: "Dual Boot WIndows XP (internal drive), Ubuntu  (external USB harddisk)"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by infonote on 2007-06-25
Hi,

Currently trying Ubuntu using Live CD.

I have a question regarding installation. I have an internal hard drive where I want to keep Windows XP.

I have an external harddrive which contains some backups of the internal drive. In this external drive I want to install Ubuntu with a Partition e.g. 40gb for Ubuntu.

Besides this I want to have an option to dual-boot i.e. choose whether I want to load Windows XP or Ubuntu.

Is there a tutorial how this can be done.
I was following the installation of Ubuntu. It only gives me 2 options

1) Automatic installation showing internal and external drive. THis allows full partition of the drive not partial.

2) Manual.

Any ideas?

Thanks in advance.

---

### Post by Alex&amp;Linux on 2007-06-25
heyo
Not sure about this, but Ill offer my guess!
I think youll have to use the manual installation to specify another disk to install on (not absolutely sure if that option is presented during the automatic installation)

If you cant see the option to do so, perhaps your usb is not detected, and thats a whole other can of worms.

Personally, I'd just cut to the chase and use your entire disk onboard for Ubuntu, as youll likely not be using windows too much longer anyhow!

---

### Post by Adrian on 2007-06-25
my freind dont bother you can have ubuntu as a file on windows by using WUBI type wubi into your search engine and see... its a free programme that allows you to install ubuntu and use it AS A FILE ON WINDOWS....so when you boot up your computer you are given the option of choosing your operating system ..but without the need for a partition ..fear not im using this right now and NO it does not damage your windows installation and if you decide that you dont like it(HIGHLY UNLIKELY I THINK)you just go into the control panel on windows click add remove programms and remove wubi from the list...easy :D best wishes adrian banbury uk (yes uk not sweeden):D

---

### Post by Adrian on 2007-06-25
infonote .....ho visto che stai a malta quindi se preferisci parlo anche italiano:D tanti saluti ...adrian

---

### Post by floke on 2007-06-25
Never used Wubi so can't comment on that.
As for the USB:
(1) Make sure you can boot from a usb in your bios or startup - if not then forget it.
(2) Install using the alternative installer - this gives you the option as to where to install grub - you do not want this on your MBR but want to put it on your external hard drive - plug it in while running a liveCD - then open a terminal and type 'sudo fdisk -l' - this will list your drives - the external will most likely be hdb1 or sdb1 - if so, then when the alternative installer asks you where to put grub you enter /dev/sdb or /dev/hdb - note - no numbers - this will put it on the mbr of the external drive. Then - just plug the usb in, turn pc on, and boot it up. I used to do this and couldn't tell the difference from the hard drive install. 

btw: I would read some threads around here on this subject first though  -especially this one
[http://ubuntuforums.org/showthread.php?t=464355](http://ubuntuforums.org/showthread.php?t=464355)

---

### Post by Yoooder on 2007-06-25
Floke definately has the best solution.

Basically it will make your external a portable Ubuntu machine that you can run from any usb-bootable PC, and it will leave the entirety of your Windows installation (including the Windows bootloader) untouched.

The only suggestion that I would add to floke's comment is that you add a GRUB entry to boot from your Windows drive (basically telling it to boot your 1st internal drive).  This would just add the benefit that you wouldn't need to unplug your USB drive to boot from Windows.

---

### Post by floke on 2007-06-25
As long as you put grub on the mbr of the external drive then it won't touch the mbr on the internal drive - so no issue: No USB plugged in = Windows; USB plugged in = choice between XP and Ubuntu.

---

### Post by PaulFXH on 2007-06-25
> **floke said:**
> 
(1) Make sure you can boot from a usb in your bios or startup - if not then forget it.

Actually, you can very easily get around this by creating a special boot cd.
Check this [guide]("https://help.ubuntu.com/community/BootFromUSB") which I have used myself to boot not just Ubuntu but two other Linux distros from an external drive when my computer BIOS did not recognise the usb drive as bootable.

---

### Post by ecksman on 2008-05-15
I have a dell d820 laptop with windows xp.

i installed ubuntu on an external drive.

but now when i log on without the external drive connected, i get an grub error.  i need to have the external drive connected to boot to windows or (obviously) ubuntu.

i want to have the ability to disconnect the external drive to boot directly to xp.

also, this is a work laptop, so my data is extremely valuable.

---

### Post by dblklk on 2008-05-15
ecksman is right. The automated installers will hose the MBR of the first internal drive.grub will install to the usb drive and is loaded by a small script on the first drive. The windows os, then, can only be booted from the external drive. There is a how to [here]("http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/"). Regards, Larry

---

### Post by meierfra. on 2008-05-15
ecksman: I wrote a HowTo for this situation. Click on DualTwo in my signature.

If your are using Ubuntu 8.04 you will also need to look at the post 14 in that thread.

---

### Post by NilsE on 2008-05-15
Almost everyone of these recommendations is correct so I can't add to it other than to quote what I do.

I have a Dell D620 LapTop internal drive that is XP and a bay drive which goes in the CD bay that is Ubuntu.  Whenever I install I remove the internal drive and put the Ubuntu drive in a USB enclosure so I can put my CD drive back in. I then boot from the CD and it installs on the USB drive and of course it does not touch the main drive since it is not there.  I can't use WUBI or touch the MBR on the XP drive because it is encrypted.

I then set my boot sequence to be the bay drive first (in your case it would be the USB drive) and if I want to come up in XP I hit F12 and select to boot from the internal drive if not it boots directly into Ubuntu. 

I rarely use XP except for some work stuff that requires IE with ActiveX.

---

