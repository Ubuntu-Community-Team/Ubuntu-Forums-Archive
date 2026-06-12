---
title: "Learning about GRUB - and need a bit of help..."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Prodromoi on 2008-01-15
Like the title says, I'm trying to get my head around GRUB and making mistakes...

So...  I'm learning about GRUB on my spare test machine, which doesn't really contain anything vital, just in case it all goes horribly wrong.  The machine has three internal IDE HDDs in it, each with a different OS installed.  Fortunately (and one of the reasons this is my test machine) the BIOS has a very nifty feature where during boot up you can choose which HDD it boots from without needing to go into the BIOS, thus making it ideal for a multiple OS machine without needing a software bootloader like BootMagic (which I've used on Windows) or GRUB.

But I wanted to learn about GRUB anyway, since one day that machine will shuffle off to the parts box in the sky...

HDD 0 already had WinXP installed, and HDD 1 already had Ubuntu Studio 7.10 installed.  I recently installed Ubuntu 8.04 on HDD 2 and this is where it's started to act up.  When I installed 8.04 I did *not* deactivate the other two drives, which I would normally do when installing an OS (as a result they would all retain individual MBRs) - instead I wanted to use the GRUB loader.

After installation of 8.04 all initially seemed fine - I was presented with a GRUB OS loader menu and selecting the appropriate OS worked fine.  (I'd have liked the GRUB options to be onscreen for longer, but that's a different question!)

But... now the WinXP installation is unstable and invariably locks up after a few hours, even if it's not actively being used, needing a soft boot to reset it.

So I pulled out HDD 2 containing the 8.04 install, with the intention of installing 7.10 to see if it's a problem with the 8.04 GRUB.

But... having done that, when I power up the machine I don't get *anything!*.  The monitor doesn't detect any video input. the start up "bleep" doesn't sound and I don't get the NVRAM check screen, etc, etc.  Putting HDD 2 back, means it boots up as it did.

So, questions...

When 8.04 was installed onto HDD 2, were the MBRs of HDD 0 and HDD 1 modified?

What on earth is happening that removing a hard drive means that the machine is not even loading up the BIOS properly?  I would have thought any error resulting from my taking this drive out would have happened *after* the BIOS screen and drive detection. 

If you've managed to read to the end of this post (which is longer than I'd planned) then thanks...!
Any suggestions and information welcomed.

---

### Post by VON_CAPO on 2008-01-15
> **Prodromoi said:**
> 

So I pulled out HDD 2 containing the 8.04 install, with the intention of installing 7.10 to see if it's a problem with the 8.04 GRUB.

But... having done that, when I power up the machine I don't get *anything!*.  The monitor doesn't detect any video input. the start up "bleep" doesn't sound and I don't get the NVRAM check screen, etc, etc.  Putting HDD 2 back, means it boots up as it did.

It looks like you forgot to move the hard drives's "jumpers" : MASTER - SLAVE - CABLE SELECT

---

### Post by VON_CAPO on 2008-01-15
Are those disk ATA?

---

### Post by Prodromoi on 2008-01-15
No, the jumpers don't need moving.

Yes, the drives are ATA.

---

### Post by VON_CAPO on 2008-01-15
When you turn on the machine, the first step is to read the instructions to check the hardware (this instructions are hard coded into a chip called BIOS).
After the BIOS check, the next step is to read the MRB (Master Record Boot) to load the operating system (the GRUB step).

You had already explained that your machine did not sound the "Beep" neither has video.
 It is clear that the problem is not related to GRUB, but the BIOS.
Also, I can guess (almost I can bet) that the "hard disk activity's" yellow light is permanently ON.
If this is the case, i believe you have to enter to the BIOS dialog and to select the right disk as bootable.
Check also, if it is the case, the order to boot, for example
1- CDROM
2- ATA
3- SATA or SCSI
4- Network
5- USB
   
If nothing works, then reboot and reset the BIOS to the factory's values.

---

### Post by Prodromoi on 2008-01-15
Well, that's helped somewhat.

My boot order was as I had set it in the BIOS previously:
1. Floppy
2. CDROM
3. IDE 0

(and the drive I had removed was IDE 2)

The error that I had made was (rather foolishly) that I had removed the drive's molex power plug but not the IDE cable.  (Usually I remove both but had forgotten this time.)

However... this still leaves two questions.

1.  Why would installing 8.04 onto HDD 2 - and thus installing GRUB - result in the WinXP installation suddenly becoming unstable?  (I don't use the WinXP much, and certainly for nothing likely to cause it to become brittle.)

2.  Having fully removed HDD 2 I got a GRUB error on boot up (replacing HDD 2 meant the error stopped).  This seems to indicate that installing 8.04 on HDD 2 also created changes on the MBR sectors of HDD 0 and HDD 1.  Is this correct?

---

### Post by dstew on 2008-01-15
> Why would installing 8.04 onto HDD 2 - and thus installing GRUB - result in the WinXP installation suddenly becoming unstable?This is hard to figure out. One thought is that HDD2 and the BIOS talk to each other occasionally. Maybe the drive has some error-checking software that is running. Hard to say.
> This seems to indicate that installing 8.04 on HDD 2 also created changes on the MBR sectors of HDD 0 and HDD 1. Is this correct?Yes, this is correct, but it probably put its stage1 boot loader into only one of the other disks' MBRs. When grub is installed, it puts stage1 on the MBR of the disk you designate during installation. The default is (hd0), which is usually the first IDE disk. Sometimes, it is whatever disk the BIOS has designated to boot. When grub stage1 runs, it loads into memory and executes stage2, which is stored on the Ubuntu root partition. If you remove the disk that has the stage2 part, grub is very limited in the error codes it can produce. It might give you only a number with no explanation.

---

### Post by Prodromoi on 2008-01-15
> **dstew said:**
> Yes, this is correct, but it probably put its stage1 boot loader into only one of the other disks' MBRs. When grub is installed, it puts stage1 on the MBR of the disk you designate during installation. The default is (hd0), which is usually the first IDE disk. Sometimes, it is whatever disk the BIOS has designated to boot. When grub stage1 runs, it loads into memory and executes stage2, which is stored on the Ubuntu root partition. If you remove the disk that has the stage2 part, grub is very limited in the error codes it can produce. It might give you only a number with no explanation.

Ah, I see.  I had expected it to only modify the MBR on the HDD where the OS was being installed, and no other/s.

So... I'll work out which MBRs need fixing (tomorrow - it's too late now and my mind is beginning to shut down!), fix them and then change the order that the drives are in.  I'll probably go for:

IDE 0 - 8.04 (or whatever OS I'm playing with at the time)
IDE 1 - WinXP
IDE 2 - Ubuntu Studio

My thinking here is that it'll be IDE 0 that I'm tinkering with most of the time so that should (I hope) confine the MBR changes to that one.  And if not, because the BIOS has its own boot menu if the install or MBR on IDE 0 gets trashed, I can pull it out and still boot from either of the remaining drives.

---

