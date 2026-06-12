---
title: "Install Failure malloc: 3 0x0 -0x0"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by sharkey77 on 2006-05-30
AMD k6 300
128 MB RAM
2.0 Gig hard Drive
Edubuntu 6.06
PC (Intel x86) alternate install CD 

I'm trying to install Edubuntu 6.06 in an older computer for my son.  I think it'd be great for him to have a learning computer (he's 4 years old and going into kindegarten in August)  I don't get very far.

ISOLINUX 3.11 Debian 2006-3-16 Copyright (c) 1994 -2005 H. Peter Anvin
Loading...
Initializing GFX code...
Static Memory: 0x40020 - 0x9fc00
         malloc 0: ox52c10 - 0x9fc00
         malloc 1: 0x800000 - 0x900000
         malloc 2: 0xa00000 - 0xb00000
         malloc 3: 0x0 - 0x0

Then the system hangs forever.

As a test I tried RH 6.2, no hang there.  

P.S. Did I miss the install forum or do these need to be better organized?

Thanks for any help.

---

### Post by Sef on 2006-05-30
1) Did you md5sum the download?

2) If so, could be a bad burn, so reburn..

3) Might also be a bad disk - may have a few bad disks, if it is.

---

### Post by sharkey77 on 2006-05-30
[QUOTE=Sef]1) Did you md5sum the download?

2) If so, could be a bad burn, so reburn..

3) Might also be a bad disk - may have a few bad disks, if it is.[/QUOTE]


I hate to admit this but I have no idea how to verify md5 in Windows XP.  I don't get far enough in the install to "Check CD for Defects"

I'll try one more burn and reply.

Thanks

---

### Post by sharkey77 on 2006-05-30
I burned another cd and got the same error, then the lightbulb came on.

I put the cd in this computer, much much newer, and ran the check cd function from here.  CD is fine.

The sad thing is this is Edubuntu I'm trying to install and I think the error is related to memory.  RH and Windows install fine on that computer.  If this software is to help resource derprived schools it's not going to get far with such hefty install requirements.  Hopefully it's a bug that just needs to be fixed. :-?

---

### Post by sharkey77 on 2006-05-30
Darn, same issue with Xubuntu 6.06 as well.

---

