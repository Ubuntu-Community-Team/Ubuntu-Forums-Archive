---
title: "Ubuntu wont boot"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Aesculaius on 2007-08-19
Ok I have a weird setup here so pay attention lol. I have a macbook that I put Bootcamp beta on to install Windows XP onto it. When I logged into windows.. i downloaded Wubi so I could install Ubuntu onto my windows partition. When I try to boot into Ubuntu.. I repeaditly get an error message refering to a partition table in drive 80. It askes me to to use a microsoft fdisk tool to rebuild it. My Windows partition's format is NTFS. Is this not going to work because its a Mac book even though im doing it on my windows partition?

---

### Post by RandomUsr on 2007-08-20
Am I glad I seen this for soooo many reasons.

OK Jesting aside, this is NOT the way to install ubuntu on Mac! Period!

The only reason an intel based mac is NOT a PC is due to it's use of EFI or Extensible Firmware Interface which controls whic OS can load and How to enumerate Hardware. What this means then is that the Hard ware isn't just a PC, it's an extension of the OS, meaning you may only install what Mac will let you install unless you can Speak to the EFI portion of the hardware. 

That being said, Boot Camp allows this interaction between Windows and the EFI module. WUBI it sounds like is searching for the Bios w/o regaurd to EFI, b/c it was not meant to handle EFI. However, Mubi, a new implementation is said to work natively on OSX. BTW, When attempting to install Ubuntu with WUBI the hardware prolly begins offering itself over and over again until you get the Disk 80 error, or maybe that's some type of install error of WUBI or Windows. 

Here are the Links that you NEED to look at to understand all of this.

EFI:
[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

Boot Camp
[http://en.wikipedia.org/wiki/Boot_Camp](http://en.wikipedia.org/wiki/Boot_Camp)

Wubi FAQ's
See Supported Platforms
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Answers.com
[http://www.answers.com/topic/wubi](http://www.answers.com/topic/wubi)


Good Luck

---

### Post by Jimmyfj on 2007-08-20
Why not just download and install Ubuntu for Mac? Should give you the best results in the long run :)

---

### Post by Aesculaius on 2007-08-20
Well.. Can I install Ubuntu for Mac so that it will run along side Mac like it would if I used wubi for windows? I just wanted to play around with Ubuntu I dont wanna dish out 80 bucks for Parallels or VMWare Fusion. And could A reason why Ubuntu wont boot is because my Windows File System is NTFS? I talked to a manager at my work today who has installed ubuntu and said that ubuntu has to be installed on a FAT32 system and NTFS wont work..

---

### Post by alienexplorers on 2007-08-20
actually Ubuntu gets installed on a ext3 partition.  Use the ubuntu for mac cd and try loading again.

---

### Post by Aesculaius on 2007-08-20
Yeah.. I  didnt understand a word you just posted.. Doesnt matter I have enough problems as it is and I think Ubuntu caused it.. my OS X partition on my Mac book isnt functioning properly and this didnt start until after my failed attempt at running Ubuntu.. so now I need to get my Macbook repaired at the store I bought it at.. and im uber frustrated..

---

### Post by s3a on 2007-08-21
If you want to avoid many problems, use Ubuntu as a Live CD! Simple ;)...until you get your problems worked out. Just save your work on permanent storage. Not on desktop, etc since that is temporarily stored in the computer's RAM.

---

### Post by josh_dye on 2008-04-18
> **Aesculaius said:**
> Well.. Can I install Ubuntu for Mac so that it will run along side Mac like it would if I used wubi for windows? I just wanted to play around with Ubuntu I dont wanna dish out 80 bucks for Parallels or VMWare Fusion. And could A reason why Ubuntu wont boot is because my Windows File System is NTFS? I talked to a manager at my work today who has installed ubuntu and said that ubuntu has to be installed on a FAT32 system and NTFS wont work..
use [http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

