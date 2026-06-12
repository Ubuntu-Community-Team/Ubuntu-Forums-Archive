---
title: "terrible, terrible problem"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by andrewbossie on 2008-12-16
ok, so yesterday i decided to wipe out my two partition scheme on my macbook. i proceeded to reinstall osx off of my external firewire dvd drive because the internal drive in my macbook is messed up beyond belief. after wiping my hard drive clean (i already backed up) the install hanged because apparently the disk was scratched. i managed to get a hold of an older tiger install disk and installed that. now i want to install ubuntu on the whole drive but ubuntu isnt bootable from the firewire drive (doesnt recognize it) and i cant boot it from my internal one. i hate using tiger, is there any way i can install ubuntu without a cd? :mad:

thanks in advance!

---

### Post by theozzlives on 2008-12-16
I don't think so. I don't know much about Macs but check to see if there's an option to boot from Fire Wire.

---

### Post by cyberdork33 on 2008-12-16
> **andrewbossie said:**
> now i want to install ubuntu on the whole drive but ubuntu isnt bootable from the firewire drive (doesnt recognize it) and i cant boot it from my internal one. i hate using tiger, is there any way i can install ubuntu without a cd? :mad:

In your situation, no. You need to download the iso, burn it, and reinstall. You can then get files from your old installation off the external drive.

---

### Post by andrewbossie on 2008-12-16
ok so i used target disk mode to install ubuntu from another mac. but when my computer boots up nothing happens. ubuntu is there but i cant boot anything. any suggestions?

---

### Post by cyberdork33 on 2008-12-17
> **andrewbossie said:**
> ok so i used target disk mode to install ubuntu from another mac. but when my computer boots up nothing happens. ubuntu is there but i cant boot anything. any suggestions?

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by andrewbossie on 2008-12-17
thanks for the link but im not dual booting, will i still be able to install refit on a single boot ubuntu machine?

---

### Post by StephenD on 2008-12-18
Not sure if it is possible in your case, or at all for that matter.  But I would try booting with the CD on another computer and trying to make an install disk on a flash drive.

---

### Post by cyberdork33 on 2008-12-19
> **andrewbossie said:**
> thanks for the link but im not dual booting, will i still be able to install refit on a single boot ubuntu machine?

In that case, did you convert the drive from a GPT disk to a normal MBR disk first? That will simplify matters for the single-boot. You can do this in gparted, but it will wipe you current disk partitions!

---

### Post by andrewbossie on 2008-12-21
honestly i ddint even know to do that. can i do that if i reinstall ubuntu? and just as an update, grub boots to the ubuntu version selection screen, but when i select it, i get an error.... 21 i believe. i tried grub setup from the command line but it didnt change anything.

---

### Post by pxwpxw on 2008-12-21
> **andrewbossie said:**
> honestly i ddint even know to do that. can i do that if i reinstall ubuntu? and just as an update, grub boots to the ubuntu version selection screen, but when i select it, i get an error.... 21 i believe. i tried grub setup from the command line but it didnt change anything.

If you are seeing the grub command line or its menu when you restart the macbook, then you should be able to boot ubuntu from the macbook hard disk without needing refit, if ubuntu is there.
But what version Ubuntu did you install? - usually there is a problem with Hardy804 or Intrepid810 that needs refit's partition sync before you could get grub to load, but you dont seem to have that problem.

Have you still got Macosx Tiger on the Macbook?
If you have Macosx, could you post your disk partiton layout from Macosx terminal command line -
```

 diskutil list

```

===

---

### Post by andrewbossie on 2008-12-22
im have 8.04 installed.

/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *232.9 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:   Microsoft Basic Data                    195.6 GB  disk0s2
   3:              Apple_HFS Untitled 2         34.7 GB   disk0s3
   4:             Linux Swap                    1.9 GB    disk0s4
 
that microsoft basic data is my ubuntu partition. i dunno why its says that.

---

### Post by pxwpxw on 2008-12-23
> **andrewbossie said:**
> im have 8.04 installed.

/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *232.9 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:   Microsoft Basic Data                    195.6 GB  disk0s2
   3:              Apple_HFS Untitled 2         34.7 GB   disk0s3
   4:             Linux Swap                    1.9 GB    disk0s4
 
that microsoft basic data is my ubuntu partition. i dunno why its says that.


It seems that you have Macosx Tiger on the Macbook, and also ubuntu.
 
If that is correct, you just need to download and install refit on Macosx, and run the Partitioning Tool to restore the MBR partition table.

In Macosx go to the rEFIt web site.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

download the rEFIt-0.12.dmg (6.5M Mac disk image) and install it in Macosx.

(read the instructions on the refit site and in the package)

Then restart and run the [ Partitioning Tool ] icon from the refit screen.

Then restart and see what you get.

---

### Post by andrewbossie on 2008-12-24
yeah i already knew i had osx on my macbook as well. ive installed refit and ran the partitioning tool, and still i have the error problem.

---

### Post by andrewbossie on 2008-12-24
so i finally figured it out, apparently grub was trying to boot the wrong partition. so if anyone else is having the same problem, heres how to fix it. from the grub menu press e to edit the boot commands, select the first one which in my case was "root (hd1,1)" and change it to your selected partition, which in my case was (hd0,1). Press enter and then b to boot. 


thanks for everyone's help.

---

