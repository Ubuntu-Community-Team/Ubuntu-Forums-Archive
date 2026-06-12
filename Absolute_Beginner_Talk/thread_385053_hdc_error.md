---
title: "hdc error"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-03-15
I'm getting an error up when i try to install ubuntu 6.06 :

Buffer I/O error on device hdc, logical block 254575
SQUASHES error: Unable to read fragment cache block [1edfe744] 
SQUASHES error: Unable to read page, block 1edfe744, size ed1e

I can run ubuntu off the cd and I have xumbuntu installed on this HD can someone help me please?

1.3mz Amd, 256 ram.

---

### Post by chewearn on 2007-03-15
Did you do a LiveCD integrity check?  (One of the start-up option).

---

### Post by heatrag on 2007-03-15
ahh, coming up with the same error, So is it the cd? I assumed hdc was my Hard drive. I got the cd through the post.
oh, sorry it hadn't finished, it carried on to open ubuntu, running off the cd I suppose.

---

### Post by chewearn on 2007-03-15
Yup, probably the CD is not good.  Unless your drive is old and having problems on other discs as well.

---

### Post by heatrag on 2007-03-15
Thanks for that. However I've done a stupid thing, I noticed the Install icon on the decktop and tried that. I'ts hung at 63%.

---

### Post by heatrag on 2007-03-16
I've replaced my drive with a CD-RW but now when I try to boot I get 

GRUB loading, please wait...
Error 15

Any help much appreciated, I lost my Xubuntu install disc and its over written on the HD now.

---

### Post by chewearn on 2007-03-16
> **heatrag said:**
> I've replaced my drive with a CD-RW but now when I try to boot I get 

GRUB loading, please wait...
Error 15

Any help much appreciated, I lost my Xubuntu install disc and its over written on the HD now.

Is that what you get when you boot from the LiveCD?  Did you get a new disc?

If you got that when boot from HD, I think error 15 means file not found.  It probably means your HD partitions are still intact, but the menu.lst cannot be found.  So, the installation is not completed.

If you originally have another OS on the HD, you can (likely) still be able to recover them.  Only you need to restore your MBR.  If you want to do that, if for Windows, you can download the fixmbr recovery
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

If not, and you want to install ubuntu straight away, I suggest you download the ubuntu iso and create a fresh disc.  Then, before you go into installation, check the disc first.

---

### Post by heatrag on 2007-03-17
I'm not sure where it's trying to boot from, there's not much activity from the cd drive. I'm sure there is nothing wrong withthe ubuntu disc(s), I've downloaded another and I think I know what the problem was withmy origional posted cd, it had a dirty spot, that did boot but dosn't now. So here I have a confession to  make, I've been into the BIOS. I need help with that now.
I have my IDE Primary master as the fujitsu HD
primary slave - none
secondary Master   ATAPI DVD-ROM 12X
secondary slave   CD_RW   CDR_2440MB

Drive A   1.2 , 5.25 in
Drive B   None

Is this correct

---

### Post by chewearn on 2007-03-17
> **heatrag said:**
> I'm not sure where it's trying to boot from, there's not much activity from the cd drive.
You can tell a CD boot by looking at the screen.  Right after the BIOS boot screen, you should see a message (only for a second or two) saying something like "CD boot:".  Then, you will see the ubuntu logo on top center, with a list of menu options below it.  The first item of the menu should be "Load or install ubuntu" (or similar; I'm trying to recall from memory).

If you are booting from instead HD, you should see "Loading grub stage 1.5".  Then in dual boot case, the grub menu (all text) will appear.  For single boot ubuntu, you will get "ESC to go to boot menu" with a seconds countdown.  At the end of countdown, ubuntu logo will appear and the OS will load.

Of course, I am referring to Edgy Eft.  For other versions, this might be different; but it will still be quite simple to figure out.

> So here I have a confession to  make, I've been into the BIOS. I need help with that now.
I have my IDE Primary master as the fujitsu HD
primary slave - none
secondary Master   ATAPI DVD-ROM 12X
secondary slave   CD_RW   CDR_2440MB

Drive A   1.2 , 5.25 in
Drive B   None

Is this correct
Looks OK.  Primary IDE HD should be detected by linux as hda.  The DVD-ROM should be hdc and CD-RW hdd.

Are you planning to dual boot with Xubuntu?  You can save some space by sharing a swap partition between ubuntu and xubuntu.

---

### Post by heatrag on 2007-03-18
hello again.
I've tried ubuntu I think it's much more suited to my skill level than xubuntu so its a wipe. 
I had been doing a lot of trial and error settings in the BIOS regarding first boot. Quite often I was getting a fault on the floppy so I dicconnected it and in the advanced BIOS features configured: 
first boot device - CDROM
second boot device - HDD-0
Swap Floppy Drive - Enabled
Boot up Floppy Seek - Disabled
and on the Standard Cmos configured Drive A and B to none.
I am sure this is wrong but I was able to load ubuntu. Fantastic!!
Do you think I should leave these settings and what will happen when there is a cd in the drive when starting up? Thanks for you help it has been very valuable to me.

---

### Post by chewearn on 2007-03-19
> **heatrag said:**
> I had been doing a lot of trial and error settings in the BIOS regarding first boot. Quite often I was getting a fault on the floppy so I dicconnected it and in the advanced BIOS features configured: 
first boot device - CDROM
second boot device - HDD-0
It a matter of personal choice, but I always removed CD-ROM from boot device list once I'm done.  Thought the system should be able to ignore non-bootable CD and skip to the HD, the downside is your boot time might take slightly longer.  Also if you have a bootable CD in the drive, you might inadvatently boot from the CD.

>  Swap Floppy Drive - EnabledThis is a legacy feature, from the days when there is still 5inch and 3.5inch floppies co-existing.  I'm not sure how linux read this, but in Windows, this merely swap A: and B: around.

> Boot up Floppy Seek - DisabledThis remove the annoying "floppy grinding sound" everytime you boot up.

> and on the Standard Cmos configured Drive A and B to none.
I am sure this is wrong but I was able to load ubuntu. Fantastic!!Glad it is working for you.:popcorn:

> Thanks for you help it has been very valuable to me.No problemo.:biggrin:

---

### Post by justleen on 2007-03-19
> **heatrag said:**
> 
Do you think I should leave these settings and what will happen when there is a cd in the drive when starting up? Thanks for you help it has been very valuable to me.

You can leave these settings. However, when your system finds a bootable CD< it will try to boot from it. In case of a Ubuntu CD: it will boot the Ubuntu Live cd.

Best is, once your done with the install, to make the hard drive the primary boot, so you dont have the problem of "spontanious CD boots"

---

