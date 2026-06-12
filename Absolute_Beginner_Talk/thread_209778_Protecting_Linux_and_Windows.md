---
title: "Protecting Linux and Windows"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by mit on 2006-07-05
I am about to wipe my machine and partition it for Kubuntu and XP. I might put a FAT32 partition in too for sharing files between them.

The plan was to use Kubuntu's built in utility to back up (without a restart?) and Acronis 9 for the windows side of things.

What is the best utility to use to format and partition the drive? Last time i did it i used XP to install itself first and partition the drive.  Once installed i booted from Ubuntu and choose to install from the spare partition created during the XP install.

Is this the best way of doing things?  The plan is to keep XP Pro on for work purposes and learn Linux too.

The idea being, if i screw up i can always restore the work image using Acronis...

Thanks for reading :KS

---

### Post by shoot2kill on 2006-07-05
what i did when doing the same thing as you plan to....

install XP using half of the HDD with FAT32 format

install ubuntu on the second half using live CD

then mount XP drive on ubuntu...

ubuntu can handle the XP installation very well... XP does not like ubuntu.... i would do this, if you want any more info, just ask...

:)

---

### Post by mit on 2006-07-05
Hi there,

Thanks for your reply. You have lost me on the answer though #-o 
I will need to have XP on an NTFS partition due to joining a domain and file permissions etc....

Mit

---

### Post by shoot2kill on 2006-07-05
sorry for confusion... 

i found the best way of dual booting is to use the operating systems own partitioning program...

install XP using 50% of the available disk space using XP partitioner.....

install ubuntu/kubuntu using the other 50% of the disk space using the default partitioning software in the live CD....

if you install XP as NTFS, you will not be able to SAFELY modify write to the windows partition....

---

### Post by mit on 2006-07-05
Hi,

That is what i will do, use their own partitioning tools..
As for installing XP on NTFS, as long as i have no need to access XP from Ubuntu that will work fine won't it?

mit

---

### Post by shoot2kill on 2006-07-05
yes ofcourse... you can access/read the NTFS partition but u cannot write or modify the files on it...

i thought i would be fine this way with NTFS, but now it would have really come in handy to use FAT32...

just a thought, and glad i could have helped...

---

### Post by mit on 2006-07-05
thanks for your help. :KS 

Mit

---

