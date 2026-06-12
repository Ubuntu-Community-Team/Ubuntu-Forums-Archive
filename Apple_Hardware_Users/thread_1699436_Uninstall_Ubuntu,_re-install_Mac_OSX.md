---
title: "Uninstall Ubuntu, re-install Mac OSX"
date: 2011-03-03
forum: Apple Hardware Users
---

### Post by NurthinAziz on 2011-03-03
Running Ubuntu 10.04 and I'm trying to re-install Mac OSX back onto my MBP. I'm running competely off of GRUB and I have no other partitions for any other OSs running. Popped in my MAC OS CD and came up with this error.

Unable to mount location
Error mounting: mount exited with exit code 1: helper failed with:
mount: block device /dev/sr0 is write-prtected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

How should I go about with removing Ubuntu, and re-installing MAC OSX?

---

### Post by srs5694 on 2011-03-03
That sounds like a Linux error. My suspicion is that you've still got GRUB installed on your hard disk and it's managed to boot whatever remnants of Linux exist far enough to produce an error message. If so, you should probably try holding down the Command key (or is it the Option key? I can never remember...) while booting the computer. That should produce a boot prompt that will enable you to select the CD/DVD drive rather than the hard disk as a boot device.

---

### Post by macbookproi7 on 2011-03-04
Have you tried doing what srs mentioned? Restart your MBP with your Mac installation disc in (I'm assuming you have an intel based MBP) make sure it's the installation disc that CAME WITH YOUR MBP.... a normal installation normally won't work as the discs are licenced to the computer. Hold down 'option' key, untill it opens a boot option screen.
It should give you the option to boot from your HDD which will be your Ubuntu Linux OS, or the disc will show up. Select the disc and boot from that. When it opens and asks you if you would like to insall Mac OS, click up the top in 'Utilities' and go to 'Disc Utility'. Select your HDD from the left panel, and erase it... ensuring it is formatted into the top option.. Journaled or something (the quick one). This will erase your Ubuntu installation. 
Then exit Disc Utility, and if you have a Time Machine backup you can either go back up to Utilities and restore your computer from a Time Capsule backup to a previous condition... or do a clean install by just clicking Continue where it asks you if you would like to install and follow the procedure.
If you plan on installing Linux OS's in future...after you have erased and formatted your drive.. I would suggest Partitioning it so you have a Partition for installing your Linux OS's, I am new to Linux and have a 500gig HDD so I gave myself a partition of 120gig for installing Linux.
Hope that helps.

---

### Post by NurthinAziz on 2011-03-06
Popped in the DVD. Getting a prohibitory icon. :(

---

