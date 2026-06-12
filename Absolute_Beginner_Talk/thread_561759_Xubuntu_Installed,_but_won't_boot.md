---
title: "Xubuntu Installed, but won't boot"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by GroupB on 2007-09-27
Hello,
I''m brand spanking new at this.  I have an old 1999 Dell Precision 410 desktop which was a hand me down several times (had been modified several times over the years with extra CD drives, RAM, and such, but I don't know exactly what was changed).  It currently has 256 MB RAM, Pentium II, and originally ran Win98, but I guess someone upgraded to Windows 2000 at some point.  

I would like to get away from Windows on my main computer, so thought this old one would give me a chance to learn Linux instead of just playing with the LiveCD.  So, I thought I would try to make use of it by installing Xubuntu (no dual boot or anything else fancy, just a clean install).  First, Xubuntu 7.04 wouldn't boot from the live CD (it gave me an error, and online I found out it something to do with the updated kernel, so a few folks suggested I try 6.06 LTS).  That worked, and I installed Xubuntu just fine.  The only strange thing I noticed during the install is that originally under Windows, the computer had only a single 20GB hard drive, but the Xubuntu installation GUI displayed 2 hard drives (sda and sdb), each 10GB, and asked which one I wanted to install under.  I tried the 1st one, and hit go.  It installed fine, but after the re-boot, the Dell splash screen comes up, the BIOS seems to load, but I get a message saying "No boot device available.  Press F1 to retry and F2 for options".  F1 didn't work, and F2 just took me into the BIOS menu to change boot order, time, and such.  So, I'm stuck.  I tried to reboot off the live Xubuntu live CD and installed again, except this time tried the other hard drive.  It installed fine, but same error message came up upon reboot after the install.  Any help would really be appreciated.  Thanks.

---

### Post by overdrank on 2007-09-28
Hi I would suggest using the alternate cd found here
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/)
And it is a text install since you are not wanting to try the live cd this way when you install you can delete all the partitions on the hard drive and do a fresh install that will hopefully over write the drive and let the grub control the boot. You can try this method with the current disc you have just choose manual and delete all the partitions and create a new partition. Hope this helps good luck!

---

### Post by GroupB on 2007-09-29
Thanks for the advice.  The thing is though their are no partitions as far as I can tell (I think the machine has 2 physical hard drives inside).  Maybe I should crack open the box to see.  Could having 2 internal drives effect the boot up process?  

Anyhow, upon startup, after the Dell screen, the machine says something about an Adaptec Array1000 family BIOS, and then SCSI Utility (which shows two hard drives).  After that, it use to boot into Windows but now, after my Xubuntu install, it says "No boot device available".  During startup, there was an option to enter the SCSI utility with F6, so after my previous failed Xubuntu install, I hit F6, and in there I was able to re-format both hard drives.  Hopefully it is 100% clean now.  I am currently running the live CD and trying an install one more time again.  I have no idea what I am doing, but I guess this is how one learns.  Its nice to have a computer I don't care about!

Any other thoughts would be appreciated.  

PS - Anyone know why the Xubuntu and Ubuntu 6.06 LTS Live CDs will both  boot in my machine, but neither Live CD distro in the 7.04 version will boot?

---

### Post by overdrank on 2007-09-29
> **GroupB said:**
> Thanks for the advice.  The thing is though their are no partitions as far as I can tell (I think the machine has 2 physical hard drives inside).  Maybe I should crack open the box to see.  Could having 2 internal drives effect the boot up process?  

Anyhow, upon startup, after the Dell screen, the machine says something about an Adaptec Array1000 family BIOS, and then SCSI Utility (which shows two hard drives).  After that, it use to boot into Windows but now, after my Xubuntu install, it says "No boot device available".  During startup, there was an option to enter the SCSI utility with F6, so after my previous failed Xubuntu install, I hit F6, and in there I was able to re-format both hard drives.  Hopefully it is 100% clean now.  I am currently running the live CD and trying an install one more time again.  I have no idea what I am doing, but I guess this is how one learns.  Its nice to have a computer I don't care about!

Any other thoughts would be appreciated.  

PS - Anyone know why the Xubuntu and Ubuntu 6.06 LTS Live CDs will both  boot in my machine, but neither Live CD distro in the 7.04 version will boot?

Hi I have heard that dell does use raid in there systems but with those small of hard  drives I would think that it is just partitions. It may be some issue in the bios that will not allow the feisty cd to boot. Also could be a bad download and you can check the checksum using this link
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also if you could post the output of the command 
```
lspci
```
this will identify your hardware and we can help and search for issue's.

---

### Post by GroupB on 2007-09-29
Thanks so much for the help (this community is great).  I gave up on Xubuntu since it still would never boot after installation, so I tried Ubuntu 6.06.  The install worked, and I'm writing this message from my "new" (i.e. 1999) computer!  After that, I read these forums, and was able to figure out how to install the Xfce environment on top of that, and this old machine is much quicker.  It is faster than my 2005 Windows XP computer. 

I still would like to run 7.04 instead of 6.06, but like I mentioned, I never could get the Live CDs of any 7.04 version to boot to work (tried both Xubuntu and Ubuntu).  I put that command in you said, and here is the output.  I'll also follow the link you said to check if my 7.04 downloads are okay.  Any thoughts would be appreciated.  Thanks!

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0d.0 SCSI storage controller: Adaptec AHA-7850 (rev 03)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone]
0000:00:13.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:01:00.0 Display controller: Texas Instruments TVP4020 [Permedia 2] (rev 01)0000:02:06.0 Memory controller: Adaptec AIC-7815 RAID+Memory Controller IC (rev 02)
0000:02:0a.0 SCSI storage controller: Adaptec 78902
0000:02:0e.0 SCSI storage controller: Adaptec AIC-7880U (rev 01)

---

