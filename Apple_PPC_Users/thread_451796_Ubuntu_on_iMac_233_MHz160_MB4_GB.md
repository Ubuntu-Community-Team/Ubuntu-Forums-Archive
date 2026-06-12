---
title: "Ubuntu on iMac 233 MHz/160 MB/4 GB"
date: 2007-05-22
forum: Apple PPC Users
---

### Post by iMac233 on 2007-05-22
Hi,

I am trying to install Ubuntu on iMac 233 MHz/160 MB/4 GB [Tried with ubuntu-6.06.1-desktop-powerpc.iso]

And not sure how to proceed after 'ramdisk is loaded' message is displayed at the command prompt…

Following are the details and steps followed:
-	iMac is running Mac OS 8
-	Booted with ubuntu-6.06.1-desktop-powerpc CD [by holding down ‘c’ during start]
-	This take me to the “Boot:” prompt
-	On tying Help it shows list of available images
-	On entering image name [live-powerpc or live-nosplash-powerpc] it shows following messages and halts at ‘0>’ prompt:
Boot: live-powerpc
Please wait, loading Kernel…
Elf32 kernel loaded…
Loading ramdisk…
ramdisk loaded at 01900000, size 8409 kbyts
Default catch!, code=300 at %SRRO; ff808944 %SRR; 100003030
Apple iMac Open Firmwire 3.0 f8 built on (date & time…..)
Ok
0>
 
So what should be done next to install Ubuntu on this iMac? Is this a problem or it just needs next set of commands to proceed and what would be these commands? 
Is there a GUI based Ubuntu installer for iMac(G3)?

:)

I will keep trying with the hope to get answers from you wise guys on this ….

---

### Post by Auria on 2007-05-22
The LiveCD is all graphical (this is the one you have, however it seems to have problems with your hardware), the alternate is command-line.
For old computers the alternate is often better.

Also, be sure to check the PPC faq (its a sticky) it's got loads of info

---

### Post by iMac233 on 2007-05-22
Thanks for a response Auria...

I found great info put together by ZoiaGuyver at... it sounds wonderful and I am going to try it ...
[http://ubuntuforums.org/showthread.php?t=405934&highlight=imac](http://ubuntuforums.org/showthread.php?t=405934&highlight=imac)

Hope this works... anyone with more detail is welcome to add suggestions and comments...

---

### Post by iMac233 on 2007-05-23
I could proceed with installation [after switching to Ubuntu 7.04]. The machine restarted after installation but it got stuck again for Default catch!, code=300 at %SRRO.............

Any suggestions how to get this resolved?

---

### Post by linear on 2007-05-25
I don't believe you can run Ubuntu with 160MB of memory...

Perhaps Xubuntu?

---

### Post by WolfHeart on 2007-06-12
I am running ubuntu fine on my imac g3 233mhz, 128 meg ram. it also runs fine on an old toshiba tecra 8000 with 300 mhz and 128 megs of ram. But i have to use the alternate install cd.

---

### Post by Enverex on 2007-06-12
The alternate install CD is always a good idea for machines that aren't really generic desktops, it's far less likely to go wrong somewhere along the way and would boot up massively faster.

---

