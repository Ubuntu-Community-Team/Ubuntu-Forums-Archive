---
title: "OsX Need help with install and duel booting abilities"
date: 2008-06-24
forum: Apple Hardware Users
---

### Post by epicbattle on 2008-06-24
Alright, I have no real clue what I'm doing. I have OsX 3.9, and I don't want to buy Leopard. Is there a way I can have both Ubuntu and Os X and just boot the appropriate operating system? I do video editing and I want to be able to use the Final Cut program, but use Ubuntu for everything else. 

Also, I have downloaded the file from three different places and OSX won't recognize any of the files. I'm not sure if it's my computer or if I am down loading the wrong files or what. If anyone has a reliable link that my 3.9 can read, it would be appreciated. 

Thank you.

---

### Post by stream303 on 2008-06-24
What model of Mac do you have?  Is it fast enough / have enough ram to actually support final-cut-pro in a real-world situation?

If you have backed up all your data, you just need to make space for Ubuntu.  You can do that by shrinking your existing Apple partition, and let Ubuntu install to the free space.  There are threads in the Apple PPC forum archives that you might want to look at, or you can use commercial utilities like iPartition.

Or, you can reinstall OSX, and just before you actually go ahead, visit the top panel and get into disk-utility.  From there, you can delete your existing partitions, and then repartition your drive, say half for OSX, and leave the rest as free space - then continue with the OSx install.  When that is done, you can install Ubuntu onto the free space, and towards the end of the Ubuntu install, the bootloader should configure itself to allow you to choose either Ubuntu or OSX at startup.

---

### Post by cyberdork33 on 2008-06-24
Please specify what Mac you have and we will be able to direct your efforts better.

---

### Post by owlgorithm on 2008-06-25
One option that will definitely work is to install Mac to an external firewire hard drive and Ubuntu to the main hard drive. This will be very easy -- both installations are automated CD's. This will work for any Mac that can run Panther. If you want to keep your current installation intact but move it to the firewire disk, use [Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html").

But, if you have a laptop and you will need Final Cut Pro with you all the time, you will want to install them on the same hard drive (especially if you have a PowerPC, because booting from USB is a pain in Open Firmware).

As stated above, however, this all depends on what kind of computer you have.

---

### Post by epicbattle on 2008-06-26
Sorry, it's a 15'' Powerbook (PPC?) G4, 1.5 GHz, 1 gig ram. OsX 10.3.9 (Panther). Kernel version Darwin 7.9.0. It does not have the intel processor. I actually have no idea what kind of processor it has. I'm new to this.

---

### Post by stream303 on 2008-06-26
It's a PowerPC (PPC) processor all right.  Sounds like you are good to go, all you have to do is make some space for Ubuntu (either shrink your existing OSX, or reinstall it to only half the drive for instance), and off you go...

---

### Post by owlgorithm on 2008-06-26
The way to accomplish what you have asked to do (run Ubuntu but retain the ability to use Final Cut Pro) is to download and boot from the Ubuntu LiveCD ([https://help.ubuntu.com/community/LiveCD]("https://help.ubuntu.com/community/LiveCD")) by holding C at startup.

Then, run GParted as in these directions ([http://ubuntuforums.org/showthread.php?t=89960)]("http://ubuntuforums.org/showthread.php?t=89960)")) and you will be able to create an empty partition on which to install Ubuntu.

---

