---
title: "Just want some clarification b4 installing gutsy"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Ippiki_Okami on 2008-01-14
hey everyone!

just wanted to get some clarification before i attempt to install gutsy on my new computer. Im new to ubuntu and the whole linux scene in general so just want to make sure i have everything right in my head first.

So basically... i have a new computer i had built with vista installed on a 320gb sata drive. i want to install a second 320gb drive, install gutsy to it, and set up a dual boot. 

so does this seem like the right things to do:
+physically installl second drive (obviously)
+provided drive is recognised etc... do i touch it in any way with vista? (format etc) or do i boot up the live cd and go straight to installation?
+ installation... chose manual parition management and choose largest unallocated space
+ once installation is completed... then edit my grub file to setup boot

sorry for the long post... i just like to have everything clear in my head... lol

thanx!

---

### Post by PeterJS on 2008-01-14
> **Ippiki_Okami said:**
> hey everyone!

just wanted to get some clarification before i attempt to install gutsy on my new computer. Im new to ubuntu and the whole linux scene in general so just want to make sure i have everything right in my head first.

So basically... i have a new computer i had built with vista installed on a 320gb sata drive. i want to install a second 320gb drive, install gutsy to it, and set up a dual boot. 

so does this seem like the right things to do:
+physically installl second drive (obviously) 
+provided drive is recognised etc... do i touch it in any way with vista? (format etc) or do i boot up the live cd and go straight to installation?

You can boot to vista confirm that the system can see the hardware, but you're going to reformat it shortly during the install, so vista drivers aren't critical.
> 
+ installation... chose manual parition management and choose largest unallocated space

Only if the drive is unformatted, most drives these days are sold pre-formatted ntfs. You could delete the parition, confirm it, go back a step, and then choose largest unallocated space.
> 
+ once installation is completed... then edit my grub file to setup boot

That's how it worked with XP. Vista seems to be kind of hit or miss about being booted from grub, the standing recommendation that I've heard is to leave ntldr in the mbr of the windows disk, put grub in the mbr of the ubuntu disk. And then install the Arconis boot manager to manage which OS boots. I haven't done this myself, and have only heard it in bits and pieces so I might have mucked some things up in there.

---

### Post by bumanie on 2008-01-14
As you are installing on a separate hard rive, it should be OK just to go ahead with the install of gutsy. Gutsy has an in-built partition manager and therefore there is no need to touch the new hard drive with vista. If I were you , at the partition management part of the install, I would choose manual installation, ensure you have the correct hard drive selected and at the very least, I would choose to install the mandatory /root and /swap partitions, as well as a /home. /home is where you can store all your documents etc. and if anything ever goes wrong with your system, in theory you should only have to reinstall the /root partition and all your documents will be safe.
You should not have to edit grub menu. If the install goes as it should, grub will recognise vista and at boot give you the option of booting vista or gutsy. [I dare say once you are used to ubuntu , you will boot vista rarely].

---

### Post by Ippiki_Okami on 2008-01-14
thanx for the quick and helpful replies!!

just a follow up question... with wat bumanie was sayin about havin a /home parition to prevent loss of data.. once eveything was setup up with the dual boot.. 

would it be possible to have say a third drive or even just another parition to store data that was accessible to both gutsy and vista.. so that if either crashed i wouldnt lose ne data? 

thanx again!

---

### Post by PeterJS on 2008-01-14
> **Ippiki_Okami said:**
> thanx for the quick and helpful replies!!

just a follow up question... with wat bumanie was sayin about havin a /home parition to prevent loss of data.. once eveything was setup up with the dual boot.. 

would it be possible to have say a third drive or even just another parition to store data that was accessible to both gutsy and vista.. so that if either crashed i wouldnt lose ne data? 

thanx again!

That's certainly possible. There are pretty much 3 options for formatting shared drives: fat32, ext3, and ntfs. Fat32 works poorly with both operating system, and doesn't support the full range of features people are used to, but on the upside they just work. Ext3 is one of the most common native file systems for linux, there is an ext2/3 driver for windows XP @ [http://www.fs-driver.org/](http://www.fs-driver.org/), I haven't heard one way or the other if it works with vista, it supports the full range of linux features, and I believe that the only feature it's missing is ntfs permissions (do people actually use those?). And lastly NTFS works like a charm with windows, and the ntfs drivers for linux these days work pretty well, their faults are they don't work if windows has locked the driver because it's hibernating, and they don't support linux file permissions, so one set of pseudo permissions is applied across the board (root:root 777).

The other nice thing about having /home and / separate is you can do a "clean" install with out loosing any of your settings or documents.

---

### Post by bumanie on 2008-01-14
I am not sure with this will be exactly what you are after, however there is an open source project name ntfs-3g. It is included natively in gutsy and allows reading writing from ubuntu to xp and vista. "The NTFS-3G driver is an open source, freely available read/write NTFS driver for Linux, FreeBSD, Mac OS X, NetBSD, and Haiku. It provides safe and fast handling of the Windows XP, Windows Server 2003, Windows 2000 and Windows Vista file systems".
As Peter_JS said there is also a program that allows the same from windows, but like him, I'm not 100% sure whether it works with vista, but suspect, by now that it does.

---

### Post by Paqman on 2008-01-14
Another obvious disadvantage of using FAT32 or NTFS for a shared data partition is that they will require defragging (although much less so for NTFS). However, pending an EXT3 utility for Vista you might be stuck with that.

---

### Post by Ippiki_Okami on 2008-01-14
thanx for all ur help so far everyone!

just one last question (for now lol)....

say i create the live cd... boot from it etc... if the live seesion is all working well is that a good indication that my hardware is all supported? 

thanx again

---

### Post by PeterJS on 2008-01-14
That would indeed be a good indication that all is going well with your hardware, that's a big part of the reason the install CD is setup to have a live environment.

---

### Post by Ippiki_Okami on 2008-01-14
thanx again everyone! i got a bit more of an idea now.... however.. ive come up with some more questions! lol

1. am i going to have trouble booting for the live cd (and later when dual booting) because of my usb keyboard?

2. which version of the ubuntu live cd should i b downloading? 32bit or 64bit? (i have a AMD ATHLON 64 X2 Dual-Core 6000+)

thanx again

---

### Post by PeterJS on 2008-01-14
> **Ippiki_Okami said:**
> thanx again everyone! i got a bit more of an idea now.... however.. ive come up with some more questions! lol

1. am i going to have trouble booting for the live cd (and later when dual booting) because of my usb keyboard?

Nope, USB keyboards work fine.

> 
2. which version of the ubuntu live cd should i b downloading? 32bit or 64bit? (i have a AMD ATHLON 64 X2 Dual-Core 6000+)

thanx again

You've got a 64 bit system, might as well make the most of it.

---

### Post by Ippiki_Okami on 2008-01-14
thanx 

do most linux programs/packages have a 64 bit version tho? or can i instal the 32bit versions?

---

### Post by PeterJS on 2008-01-14
Most programs are open source, so what's prebuilt really isn't as important as what can be built. Since ubuntu builds all of their own packages, there's really no reason for them to build a 32 bit version, but not a 64 bit version. The only thing that jumps out in my mind as not having a 64 bit version is flash (but that's macromedia's fault, closed source), but there are instructions around for getting it installed. And if all else fails 32 bit packages can be installed, but don't ask lowly 32bit using me about it.

And google earth is 32 bit only as well.

---

### Post by Ippiki_Okami on 2008-01-14
dont really use google earth... and if theres a 32bit workaround for flash then looks like i'll b goin 64bit...

hhopefully i'll b pickin up a drive to stick gutsy on tomoz!

with wat i asked bout b4 bout the usb keyboard... i just restarted my comp... pressed F12 to get into the boot menu.. but once in there i dont seem to b able to navigate with the keyboard...

i know thats not a linux related question... but any ideas?

thanx for all your help!

---

### Post by Ippiki_Okami on 2008-01-15
ne one? lol

---

### Post by PeterJS on 2008-01-15
Sorry, you might try opening the full Bios config and trying in there. It seems that your keybaord is recognized enought to get you to the boot menu, maybe the bios well actully let you do stuff.

---

### Post by jonnywombat on 2008-01-15
To install 32bit firefox with support for java and flash then visit this [http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+3in1+installer](http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+3in1+installer)

There is a 3 in 1 installer which does the job for you.... While you are there you might wanna check out swiftweasel. This is an optimized build of firefox, and there is a version which is 32 bit running in the 64 bit environment on amd 64 processor. It is a little faster.

Once you have installed firefox then it's time to pretty it up a little visit [http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets](http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets)

Use the script there to install better buttons.

Jonny

---

### Post by 10Digits on 2008-01-18
I think u should download the 64 bit version of Ubuntu>>>>:KS

---

