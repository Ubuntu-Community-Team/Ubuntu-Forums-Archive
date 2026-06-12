---
title: "HELP! Ubuntu External HD Permanent Installation"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by skitz92 on 2007-04-30
Hey. So I run a PPC G5 and would like to give Ubuntu a try for an alternate OS when I feel like it. I have a live CD I can successfully run on my mac. I try to install it using an install icon on the desktop, but I run into an error when it comes to formatting my hard drive. I always get an error like "Failed to format partition 3 to ex3". Note, I am using an external Firewire drive. I select Guide>>Entire Disk to my external, and this message keeps popping up. Anyone know what's up?

---

### Post by dstew on 2007-05-01
What are the details of the error message? Often, this is the result of a bad block on the disk. You might have to check the disk first. Boot from the Mac OS install CD and select Disk Utility from the Installer menu. Select Verify Disk to check for errors, or Repair Disk to fix them.

---

### Post by skitz92 on 2007-05-01
No repairs were necessary on the disk... Could I just restore the image of ubuntu live onto this HD so it functions like the disk?

---

### Post by dstew on 2007-05-02
No, you really should try to install it properly. The Live CD uses RAM for its filesystem. Any program you install would disappear when you shut down.

---

### Post by goodtimetribe on 2007-05-02
> **dstew said:**
> No, you really should try to install it properly. The Live CD uses RAM for its filesystem. Any program you install would disappear when you shut down.

Totally agree that it should be installed properly. It would help us help you if you can give us what you're configuring for your partitions or any other clue.

---

### Post by skitz92 on 2007-05-02
Ok so I tried again on a different external HD. This drive is a firelite 40gb usb. I set option of install for "Guided" and selected the external disk. It was installing perfectly then at the end it got an error message that yaboot wasn't installed. Should I try again?

---

### Post by dstew on 2007-05-04
My guess is that your Ubuntu is installed correctly, but that the boot configuration is not set up right. I have no experience with Power PC Ununtu, but you might find help in the [Mac forums]("http://ubuntuforums.org/forumdisplay.php?f=133").

---

### Post by Inxsible on 2007-05-04
For the first drive that you tried on, did you make sure the drive was unmounted before you tried installing on it?

In GParted, you would have to right click on the drive and 'Unmount' it. Then and only then would you be able to format it to EXT3.

A mounted drive (mounted in any OS- in case you have multiple OS'es) cannot be formatted.

---

