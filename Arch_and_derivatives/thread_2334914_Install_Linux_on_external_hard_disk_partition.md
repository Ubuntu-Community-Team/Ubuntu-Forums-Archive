---
title: "Install Linux on external hard disk partition"
date: 2016-08-23
forum: Arch and derivatives
---

### Post by esposem on 2016-08-23
Hello everybody,
I am not an expert in Linux stuff, but I managed to install the live image of Apricity OS in a partition of my external 2 TB Hard Disk. After that, I succesfully installed the full OS in another partition of the same HD.
Until here, everything fine. The problem now is about "portability" of the OS, since with all Mac computer, I can choose which partition boot by pressing Alt + Power (and it will appear my Live partition and the Os one). 
In non Mac computer, the problem is different. I tried to change the BIOS boot order putting the USB as first one, but when I start the PC it appears "No Operative System Found" or something like that. 
What can I do to solve the problem?
In addition, I would also like to know how to rename my OS, since when I choose the partition to boot I always see "EFI boot".
Thanks a lot for your help,
Emanuele

---

### Post by oldos2er on 2016-08-23
Not an Ubuntu support request; moved to Other OS Support, Arch & derivatives.

---

### Post by yancek on 2016-08-23
Clarify a few things.  Are you saying that you are able to successfully boot the installed Apricity OS from the external drive when it is attached to the Mac but are not when it is attached to a PC?
Are you using EFI on the Mac?  My understanding is that all recent Macs use EFI.  If so, that could be part of the problem as an EFI install will have a separate EFI partition and if you don't have that on the external drive it can't be accessed.  These are just general observations of possible problems to look for as I don't use EFI and have never used a Mac.  .

Who is the manufacturer of the PC as different manufacturers have differnet BIOS options.  Did you check under the hard drive option in the BIOS to see if the usb was listed there, usually be manufactuer i.e, Sandisk, Toshiba, Lexar, etc.

---

### Post by esposem on 2016-08-24
> **yancek said:**
> Clarify a few things.  Are you saying that you are able to successfully boot the installed Apricity OS from the external drive when it is attached to the Mac but are not when it is attached to a PC?

Yes, when it's attached to a pc it appears "No operative system found" or something similar.

> **yancek said:**
> 
Are you using EFI on the Mac?  My understanding is that all recent Macs use EFI.  If so, that could be part of the problem as an EFI install will have a separate EFI partition and if you don't have that on the external drive it can't be accessed.  These are just general observations of possible problems to look for as I don't use EFI and have never used a Mac.  . 

I am not sure about EFI, I am not an expert. if you could explain better what EFI does, It would  be great. However, in my HD there is a 200mb partition called EFI, along with the 150gb partition of the Apricity Os. The remaining space are 2 other data partitions (useless). The problem, I think, is in how/which partition mark as "active" and "boot"(I guess that is needed in order to be read from a non-apple machine).
I don't know how to make the Apricity partition active since the format of that is Linux Filesystem. 
I have also found that this 200 mb EFI partition is also present in the Mac  Internal Hard Disk, but I am not sure on what it does.

> **yancek said:**
> 
Who is the manufacturer of the PC as different manufacturers have differnet BIOS options. Did you check under the hard drive option in the BIOS to see if the usb was listed there, usually be manufactuer i.e, Sandisk, Toshiba, Lexar, etc.

My idea was to create some kind of "portable" OS, where by attaching the HD to any pc (with enough hardware requirements), I am able to run my os.

---

