---
title: "Isolinux *.** Disk errror **: **** solution"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by listen on 2005-09-19
Dear all,

Do you get an error message during installation, even before the boot menu come out? The error message says Isolinux *.**, Disk error **: **** **
It doesnt matter what numbers the asterisk represent as i have faced the problem when trying to install different linux installation disc (fedora 2, 4, ubuntu 5.10)...
It seems initially that 
1. either the disc is problematic or
2. the CD-rom drive is not working/reading...

For my case, i proofed that the above 2 are not the problem by 
1. trying the disc on another computer and the boot screen came out.
2. by cleaning and checking the CD-rom by putting in data disc and read info from explorer...

SO what could be the problem... i suspected my BIOS has something to do with it...
and after downloading the new version...and flashing it...VIOLA ...the disc works fine...now i have the new UBUNTU ver 5.10 up and running.

fyi my motherboard is Aopen AX6BC Pro....i think i read somewhere in the forum that another guy solved it by flashing his BIOS too and his MOBO was an Aopen also... so maybe it is the brand...?? I dont know. 

Cheers..

---

### Post by blastus on 2005-09-19
If the CD fully works on another computer then it is either your BIOS or the CD drive. If you have a fairly new computer, (like 1999+), then you should have no problem booting with CD-R/CD-RW media. 

However some old CD drives do not support CD-R/CD-RW media. They will either read them partially and then randomly fail with errors, or sometimes read them with no errors, or not read them at all. In any case you will not be able to boot with the CD and the drive may or may not make intermittent/continual grinding noises. The fact that you can read the CD from Windows Explorer does not mean that the drive fully supports CD-R/CD-RW media--more specifically the CD-R/CD-RW media that YOU are using.

---

### Post by xmastree on 2005-09-19
[QUOTE=listen]1. either the disc is problematic or
2. the CD-rom drive is not working/reading...

For my case, i proofed that the above 2 are not the problem by 
1. trying the disc on another computer and the boot screen came out.
2. by cleaning and checking the CD-rom by putting in data disc and read info from explorer...[/QUOTE]But neither of these try **that** disc in **that** drive. A better method would be to check the disc in the drive you want to boot from, using [md5sum.]("http://www.etree.org/md5com.html") Just because a drive can read one disc, doesn't mean it can read all.
I burned a disc once, but my reader couldn't read it, although the writer could. The reader has no problem with other discs.

---

