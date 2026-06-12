---
title: "One DDR2 module or two"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by RogerD on 2007-03-04
I've been trying to install 6.06, and after that failed 6.10, on a newly built PC. The liveCD in both cases is fine, but the installation keeps failing. The motherboard is an Asus M2NPV-VM, which has four DDR2 memory slots. I specified 1GB of memory. Something tells me DDR2 memory has to be installed in matched pairs, with 1GB implying two 512MB modules. However, when I take the side off my PC case, I can only see one memory module. Is this wrong, and could it be why my installation keeps failing?

Best regards

Roger D

---

### Post by ecs_pf5 on 2007-03-04
I have got one single stick of DDR2 in mine, and although my system is having a definite problem with the video card, everything else seems fine, I can get into the command line no problem.

---

### Post by dexter on 2007-03-04
Having only one DDR2 module doesn't cause any problems. 
However when you have a matched DDR2 pair, your computer can access those two modules in parallel and will be a bit faster. 

Do you see any error messages when the installation fails ? At what point does it go wrong ?

---

### Post by RogerD on 2007-03-04
Thanks for the information on the DDR2 pair. Here's my earlier post, with all the information on the various failures I've been having:

Hi

I've just had a new PC built. Here's the spec:
Athlon 3200
1048MB DDR2 667MHz
Asus M2NPV-VM mother board
160GB SATA HD

A couple of days ago I tried to intall 6.06 using the liveCD. The liveCD bit worked fine, and I was able to open and use applications like OpenOffice Writer without any problems. Expecting that all would be well, I started the install. About 80% of the way through, I got the message"We're sorry, but the installation has failed" - never had that before. I had another go, but got the same result. I thought, maybe there was a fault on the installation CD, so I tried the DVD that comes with the book "Ubuntu Unleashed". This simply produced the message:

GRUB Loading stage 1.5
GRUB loading, please wait..
Error 15

Checking the device sequence at the boot stage, I found that the HD had priority over my DVD drive. It seemed likely that I'd got a partial installation with a faulty GRUB installation on the HD. I therefore changed the set-up to give my DVD priority over the HD. This meant, at least, that I could reliably start the liveCD.

I've filed a bug report, as requested, and been seeking help via the forum. Following suggestions, I've recently tried the 6.06 alternative CD, opting to erase the entire disk. The installation seemed to be going 'great guns', but failed at the copying files stage. I got the message:

'Configuring wvdial Installation step failed'

I then opted for "Finish installation", thinking this was the same as 'abort', and was asked to install GRUB. This didn' work, and I got the message:

"The grub package failed to install into target"

A second attempt produced very similar results

I've also tried the 6.10 liveCD, but at 'creating user' at the copying files stage, I get another installer crashes message.

It doesn't seem worth reporting this crash, all these installers can't be faulty, can they?
The most likely explanation is that there's something wrong with my new machine. Can someone please give me some ideas, so that I can either fix it myself, or go back the guys who built my machine (not Linux specialists) and tell them what to do.

Incidently, I haven't got my machine connected to the Internet during these installation attempts, but I can't believe this is the problem.

All help much appreciated.

---

### Post by omrsafetyo on 2007-03-04
Here is the error you had:

```
15 : File not found 
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.
```

In some situations, this can be fixed by booting from a GRUB floppy.
Is your floppy drive the first boot device?  If so, try giving your HDD/CD priority over the floppy.

It could also be due to a missing kernel image file - so make sure the kernel was successfully installed to your boot partition.  This could be caused by improper installation, or a bad boot partition. 

If you have the leisure, you may try wiping the HDD, re-partitioning, and starting the install all over from scratch.  But check for the FDD in the BIOS first.

---

