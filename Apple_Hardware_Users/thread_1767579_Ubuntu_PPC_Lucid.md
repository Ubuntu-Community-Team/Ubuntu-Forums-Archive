---
title: "Ubuntu PPC Lucid"
date: 2011-05-25
forum: Apple Hardware Users
---

### Post by jkzubu on 2011-05-25
I am trying to install Lucid PPC on a Mac G4 (gray & clear tower), ~1 GB RAM.  The live CD will boot and the install process will start.  Install process stops at step 4 when partition location is requested.  No partition shows.  Repeated, same results.  Removed HDD and blanked HDD (Deleted all of OSX) using gparted on my regular AMD 64-bit Ubuntu machine.  Reinstalled HDD, same results; no partition recognized...

I also did the following upon reformats; then repeated install attempts:
  Left drive blank.
  Formatted new mac partition.
  Formatted ext4
  
Same results, no partition recognized.
Any thoughts on why the drive parts will not recognize?
Should I be using a specific filesystem format? Fat, ntfs, ext2, ext3?

Thanks.

jkzubu

---

### Post by tgalati4 on 2011-05-25
I think the BIOS needs a small hfsplus partition to think that OS X is still installed (even if it isn't).  You could partition the disk using OS X's disk utility and put Tiger on only 1/2 of the disk and leave the rest of the disk unformatted.  Then use gparted from the live CD to format the rest of the disk as ext3 (if you want to be able to see the contents from Tiger) or ext4 for slightly better performance.

From that point, you should be able to install Ubuntu to the second partition.  There may be alternative boot managers for Mac to get around this limitation.  It's been several years since I played with Ubuntu on my powerbook.

---

### Post by jkzubu on 2011-05-27
Hi Tgalati4:  Than you for the input.  I originally tried to install Lucid PPC from CD while the HDD still had OSX on it.  The Lucid install from CD still did not recognize the drive.  That is when I took out the drive and reformatted a few different times/ways.  Still no luck.  The G4 machine will boot the CR Rom. So, I think the question is; how do I format the HDD so the G4 will see the partition?  I now think I need to install something like yaboot on the drive and yaboot suggests the OSX should be installed.  OSX was removed during reformat and I do not have an OSX system disk.  Any other thoughts? Thanks.

---

### Post by B_Free on 2011-05-27
The installer is bad. Install 8.04 and update from there. You maybe able to update from the cd you already have rather than the internet. There is nothing wrong with your hard drive.

---

### Post by B_Free on 2011-05-28
Did it work?

---

### Post by jkzubu on 2011-05-30
I will give it a try and post back.  Thank you, B.

---

### Post by jkzubu on 2011-06-01
Hi B_Free:

Partial Success / Partial Fail.
You were correct about using 8.04 LTS.  That did work, disk recognized and installed as expected.  The upgrade path to 10.04 LTS (From the installed 8.04) also failed, even though it went through all the expected distribution upgrade procedures.  Also, the Yaboot screen does say Ubuntu 10.04 is installed, the system is not booting into Gnome Desktop.  There are also some messages that suggest a few failures with the 10.04 install. Hmmm. 

Any other thoughts are appreciated.  Thank you.

JK

---

### Post by linuxopjemac on 2011-06-02
It sounds a little blunt maybe, but I would install MintPPC. It has so much better support for older PPC based Macs. Up to you. A lot of people are recognizing the potential of MinPPC:
[http://www.mintppc.org/content/user-experiences](http://www.mintppc.org/content/user-experiences)

---

### Post by jkzubu on 2011-06-05
Hi Linuxopjemac:

Thank you for your comment.  I have seen information about Linux Mint PPC and have tried it.  I understand that LMPPC relies on a Debian install.  I have tried DebianPPC install and it is failing on this machine.  I switched HDDs even though I agree the HDD was not the problem...  Had to try anyway.  I think the DebianPPC install is failing because of something related to an Apple bootstrap.  I am still trying, though.  The Debian (Mini.iso) seems to go through all approprate actions, but fails install at the end.  I even tried the Debian Netinst .iso (180 mb) and it will not even start the installer.  Still trying.  Thank you.  JK

---

### Post by linuxopjemac on 2011-06-06
Did you do anything special with the hard disk? Other PCI card or something like that? Try to install with only one hard disk connected as the master with the original PCI card.

---

### Post by B_Free on 2011-06-08
These are older machines. Have you replaced the battery? This has everything to do with keeping proper time. If the OS installs but fails restarting, this may solve the problem.

---

