---
title: "Running Live CD (5.10)on a Wallstreet Powerbook"
date: 2006-10-13
forum: Apple PPC Users
---

### Post by Videobeagle on 2006-10-13
I am trying to run Ubuntu 5.10 on my Wallstreet powerbook.

I have BootX 1.2.2
I'm using 5.10 becasue I found a note that 6.06 doesn't work great for Old World macs.

I found information on installing here: 
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

And one comment about running from a live cd:

>     *

      3) Add the following arguements to the boot command in BootX.

casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop -- 

I have done that, but it keeps dropping me into the install process rather than loading ubuntu from the CD.

Does anyone have any suggestions about this?

---

### Post by Frak on 2006-10-13
> **Videobeagle said:**
> I am trying to run Ubuntu 5.10 on my Wallstreet powerbook.

I have BootX 1.2.2
I'm using 5.10 becasue I found a note that 6.06 doesn't work great for Old World macs.

I found information on installing here: 
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

And one comment about running from a live cd:



I have done that, but it keeps dropping me into the install process rather than loading ubuntu from the CD.

Does anyone have any suggestions about this?
Try 6.06 first and see if that helps, because it should be the opposite, Ubuntu works better on comptuters with age, no matter what the model.

---

### Post by abtabt on 2006-10-14
do you have the right cd the LIVE CD (5.10) not the install CD ?

and do you copy ramdisk and kernel from the LIVE CD and put it in sys folder ?

some time bootex preferens file get damage trash it

and make a new one

---

