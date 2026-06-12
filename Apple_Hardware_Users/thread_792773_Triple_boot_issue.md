---
title: "Triple boot issue"
date: 2008-05-13
forum: Apple Hardware Users
---

### Post by hnlntm on 2008-05-13
Hi all me again :(

I want to run mac os x, ubuntu and yes windows xp.

after installing ubuntu I tried to boot in to windows and I get an error message regarding a missing or corrupt hal.dll.

I've had this message before and resolved it by having only one partition and running bootcamp again. However this time I think in my haste to sort the issue I've made it worse, I've removed ubuntu and refit but now when I boot in to xp it shows theres no boot device so I've reinstalled ubuntu and refit and I've got the hal.dll error again any help would be great.

---

### Post by cyberdork33 on 2008-05-13
> **hnlntm said:**
> Hi all me again :(

I want to run mac os x, ubuntu and yes windows xp.

after installing ubuntu I tried to boot in to windows and I get an error message regarding a missing or corrupt hal.dll.

I've had this message before and resolved it by having only one partition and running bootcamp again. However this time I think in my haste to sort the issue I've made it worse, I've removed ubuntu and refit but now when I boot in to xp it shows theres no boot device so I've reinstalled ubuntu and refit and I've got the hal.dll error again any help would be great.
Likely grub replaced the windows bootcode in the MBR, so removing it causes a problem with Windows...

Windows should be installed AFTER Ubuntu to avoid this issue. Some people have fixed the hall.dll issue with the following thread:
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)

---

### Post by hnlntm on 2008-05-14
> **cyberdork33 said:**
> Likely grub replaced the windows bootcode in the MBR, so removing it causes a problem with Windows...

Windows should be installed AFTER Ubuntu to avoid this issue. Some people have fixed the hall.dll issue with the following thread:
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)
Thanks I'll try this tonight and update on how I get on. Thanks again

---

### Post by sunstriker on 2008-05-14
I also installed a triple boot on my mbp.
First you download and install rEFIt in Mac os x (it's a bootloader for EFI, very good, detects every bootable device).
Then you can proceed to install ubuntu but in the final screen of the installer. Press advanced and put grub on the linux partition instead of the mbr (else you pick windows/ubuntu in rEFIt, and you'll just end up in the grub again to choose again). So you put grub in (hd0,2), if ubuntu is on the third partition on your drive (I think the 200meg EFI partition doesn't count, not sure though). This way microsoft cannot harm ubuntu and ubuntu cannot harm windows.
Anyway, there are some pretty good guides here for mac.

EDIT: the efi partition does count. So if ubuntu is on your third partition (with 1st efi, 2nd osx, 3th windows, 4th ubuntu) you have to type (hd0,3) in de advanced tab on the last screen of the installer.

---

### Post by hnlntm on 2008-05-14
Thanks again for the help I am still stuck as my windows drive in on a fat32 partition

---

### Post by kadinshino on 2008-05-16
ran into this problem my self. you have a few options. first one is, see if your mac can partition the hard drive into the following. MAC, windows, windows. that will give you one partition for XP and one for ubuntu. 

theres a few ways of doing this that i know of. the way i did was reinstalled OSX and formated my drive into 3 partitions. then i enabled the two unused partitions to target disk mode (boot camp sorta) this allowed me to choose the other to partitions in the boot menu. i installed win XP via boot camp. and all that joy that came along with it :D

then i put my ubuntu CD in and hardbooted of the CD and go to the install process. i choose my last un used disk and used ubuntu's grub boot to install a partition on the partitioned disk :D and yes it works to my amazement. *Note it had to format it to FAT16 *

---

the last way i know of doing this is installing XP via bootcamp normally giving it a big partitioned disk (40g) then once thats done boot into XP and install ubuntu as a VM. (double click the CD install wubi) 

this also worked. when you boot to XP it will then go into a second boot screen and you can choose what system you want to boot.


iv tested these two methods and both work really well. personally i like the method of installing ubuntu on the XP partition.

Hope this helps a bit :) 

PS now only if i could get the wireless to work XD

---

