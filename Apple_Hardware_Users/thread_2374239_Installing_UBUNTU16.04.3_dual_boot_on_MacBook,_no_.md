---
title: "Installing UBUNTU16.04.3 dual boot on MacBook, no HD detected only USB drive detected"
date: 2017-10-13
forum: Apple Hardware Users
---

### Post by jdv14 on 2017-10-13
Hi, I am trying to do a dual boot installation of Ubuntu 16.04.3 on my MacBook Pro (June 2017, High Sierra). I set up a FAT partition and booted into "Try Ubuntu". When I tried installing from there it is not able to detect the hard drive (SSD) and only detects the usb boot device, calling that dev/sda. When I typed in "sudo fdisk -l" it just returned the volume of the USB drive. I am wondering if the encryption of the ssd or the fact that its now APFS plays a role in this?

---

### Post by oldfred on 2017-10-14
Moved to the Apple users sub-forum as then that know the specific issues of a Mac may be able to help.

Normally you cannot install to same drive as installer. Did you create FAT partition on SSD?
You normally boot live installer from USB flash drive (or DVD).

I do not know Mac, but have a couple of links to get you started.
 [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)
[http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Install to Mac
[https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640](https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640) 
   FAT32 format  & label with boot flag on Mac
[https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation](https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation)

---

### Post by capriotti-carlos on 2017-10-16
[jdv14]("https://ubuntuforums.org/member.php?u=2079788"), hi.

Installing Ubuntu on a Mac, depending on the model, can be challenging. Adding the complexity of installing from a partition within the target disk is another step in the complexity that - trust me - you don't really want. I consider myself a fairly experienced *nix user and have tried installing from disk partition on a macmini 1,1 to no avail.

There are some good guides for Macbook Pro ([https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)), and other platforms; I suggest following them. Use a USB installer, over a USB3.0 thumbdrive if at all possible (because it is so much faster !).

With that note, you specific case does ring a bell to be; I had a Macbook pro 13-inch 2011 with a very odd - and well documented - issue: It would run fine with MacOS on its original 500 GB apple HARD  DISK, but once one tried replacing the HD with an SSD or some other HD, the disk would not be recognized at all, in any OS. 

It was the cable; Initially I did not want to believe that a cable would be selective and only allow for one disk to be detected. It turns out that the damaged cable was not able to handle higher data rates, and failed silently. 

I am only bringing this up because the case feels similar, but also because you never stated your mac's model. 

Cheers.

---

### Post by nickhell on 2017-10-22
Hi, you need a newer kernel (easiest solution) or a kernel patch. Have a look here: [https://github.com/Dunedan/mbp-2016-linux](https://github.com/Dunedan/mbp-2016-linux)
and here: [https://gist.github.com/roadrunner2/1289542a748d9a104e7baec6a92f9cd7](https://gist.github.com/roadrunner2/1289542a748d9a104e7baec6a92f9cd7)
BTW as of now sound is not working on any distro. Also suspend/resume but that is not so game changer... IMO

And depending which 14.x no wifi too, you can tether your mobile through USB though.

PD: As for now maybe its easier to try some rolling release distro as they have newer kernels. I'm quite happy with antergos (arch for newbies) KDE edition.

---

