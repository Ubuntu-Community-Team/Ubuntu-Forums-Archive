---
title: "Ubuntu 13.04 on OSX MBP and external drive"
date: 2013-07-18
forum: Apple Hardware Users
---

### Post by LionRock on 2013-07-18
Hi,

Im trying now for two days and tried everything and I cant boot to Ubuntu on external HD. On OSX Disk Utility I have created new partition on ext. HD and leave it as free space. Then I have downloaded Ubuntu desktop 13.04 and burn it on DVD. I restarted MBP and hold the "c" key to boot from DVD. Everything goes OK. I have installed Ubuntu on this free space partition (I have change it in installation process to ext4 partition type and to / as a mount point, about 250GB partition "/dev/sdb4"). I have also choose Device for boot loader installation" /dev/sdb4, so the same where installation is. I have also created a swap partition (around 10GB). Installation goes fine and everything is OK. Then I have booted to OSX and installed rEFInd which also was successfully. I have rebooted OSX and rEFInd menu appears and also a Linux partition. I have choose it and I get like "No operating system found" and also "There is no bootable device" (something like that). I have tried a lot of things and nothing works.

What Im doing wrong? 

My MBP is MacBookPro8,2" and have OSX 10.8.4

Partitions on ext. HD:
> 
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *750.2 GB   disk1
   1:                        EFI                         209.7 MB   disk1s1
   2:                  Apple_HFS External 1TB            497.4 GB   disk1s2
   3:                 Linux Swap                         10.0 GB    disk1s3
   4:       Microsoft Basic Data                         242.4 GB   disk1s4
   5: 21686148-6449-6E6F-744E-656564454649               134.2 MB   disk1s99


---

### Post by LionRock on 2013-07-19
Anyone? :/

---

### Post by coffeecat on 2013-07-19
@LionRock, you posted in the Other OS/Distro Support forum which is for any OS except Ubuntu. I've moved your thread to the Apple Users forum which is for Ubuntu on Apple hardware where it is more likely to be seen by those who can help you. Good luck.

---

### Post by saunite on 2013-08-05
Hi,

Did you check in [http://ubuntuforums.org/showthread.php?t=1046568](http://ubuntuforums.org/showthread.php?t=1046568) ? There is a part which might help you "[COLOR=#0000FF][FONT=Comic Sans MS]I installed, but Ubuntu won't boot / says "no bootable devices" / has a blinking cursor!" [/FONT][/COLOR]

---

### Post by r3dbeard on 2013-08-06
Also, there are firmware restrictions on certain models that don't allow for booting from devices connected via USB. More specifically, for some models (the MacBook Pro with Retina display, Mid 2011 and newer Macs mini, the Late 2012 iMac and all MacBooks Air) the firmware only allows for booting from external SuperDrives which require matching of other criteria specific to your device. Hope this helps.

---

