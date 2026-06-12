---
title: "IDE hard disk seen as SCSI"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by TruthOrDare on 2007-08-05
My problem seems to be an unusual one.

I have one hard disk, which is an IDE hard disk, but when I try to use the installer from the cd, it detects it as a SCSI.

I have a feeling that this is what is stopping GRUB from doing its stuff at 94%.

My current setup is this.

Windows itself: C:
Other windows partitions: D, F and G
I am trying to install Ubuntu on E: which is fine, I select the partition, make a ubuntu (ext3) partition, make a swap area and it has plenty of space to install.

I am at a loss as to why it is being detected as SCSI, this computer never has been a SCSI computer. Any suggestions would be appreciated,

Thanks.

---

### Post by Paulmd on 2007-08-05
> **TruthOrDare said:**
> My problem seems to be an unusual one.

I have one hard disk, which is an IDE hard disk, but when I try to use the installer from the cd, it detects it as a SCSI.

I have a feeling that this is what is stopping GRUB from doing its stuff at 94%.

My current setup is this.

Windows itself: C:
Other windows partitions: D, F and G
I am trying to install Ubuntu on E: which is fine, I select the partition, make a ubuntu (ext3) partition, make a swap area and it has plenty of space to install.

I am at a loss as to why it is being detected as SCSI, this computer never has been a SCSI computer. Any suggestions would be appreciated,

Thanks.

Do you have a PCI HDD controller, or more than 2 IDE ports? Sometimes they cause IDE HDDs get detected as SCSI.  (At least on Windows, though I've never heard anything bad happening as a result on Windows)

I really don't know what else to suggest. Most of my experience is in Windows.

---

### Post by Cypher on 2007-08-05
When you say IDE, is that PATA or SATA? If SATA, the newer Kernel's have migrated to using the SCSI device naming layer for them. So even though it's an IDE drive, you will be using the "sdXX" naming scheme.

@Paulmd; Hard to imagine that Windows or Linux would mistakenly recognize an IDE drive as SCSI, that's just not possible apart from the reason I gave above for Linux.

---

### Post by TruthOrDare on 2007-08-05
My hard disk is definately not SATA, 

However my motherboard (ASUS P4C800) is capable of using SATA drives.

On the partition options, it says...

SCSI1 (0,0,0) (sda) - 80.0 GB ATA WDC WD800JB-00FS

---

### Post by Cypher on 2007-08-05
I guess the Kernel must be using the SCSI naming layer for all IDE as opposed to just SATA drives..

But that's no problem, as it's just the name that has changed..

---

### Post by Paulmd on 2007-08-05
> **Cypher said:**
> When you say IDE, is that PATA or SATA? If SATA, the newer Kernel's have migrated to using the SCSI device naming layer for them. So even though it's an IDE drive, you will be using the "sdXX" naming scheme.

@Paulmd; Hard to imagine that Windows or Linux would mistakenly recognize an IDE drive as SCSI, that's just not possible apart from the reason I gave above for Linux.

In Windows, if you put a Promise IDE controller, it is ID'd as a scsi controller in the Device manager, and will identify drives attached to it as such.  It is not only possible, but I've seen it on several computers.  In Windows, it's not a problem, just an oddity.

---

### Post by asmoore82 on 2007-08-05
My girlfriend's Dell also shows an IDE drive as /dev/sda (she's running archlinux).

A thought just occurred to me when someone mentioned an ASUS motherboard with SATA ...
it may have something to do with motherboards that support IDE RAID.

---

### Post by mcduck on 2007-08-06
Kernel deveolpers recently found out that the SATA/SCSI driver also handles PATA  drives (these are the ones often called IDE drives!) better than the original PATA driver dir. So they started using SATA drivers with all drives.

That should not cause any problems, the only difference is that drives are named as sd* instead of hd*. As long as you use UUID's in fstab you shouldn't normally even notice anything.

---

### Post by TruthOrDare on 2007-08-06
So basically, Ubuntu detects the PATA and uses sda for my hard disk, but grub tries to use hd0, so maybe thats the conflict that is stopping the install at 94% with a hd0 error?

Is there any work around for it?

---

### Post by Paulmd on 2007-08-06
> **TruthOrDare said:**
> So basically, Ubuntu detects the PATA and uses sda for my hard disk, but grub tries to use hd0, so maybe thats the conflict that is stopping the install at 94% with a hd0 error?

Is there any work around for it?

If McDuck is right, the change is recent. Which means the solution may be to downgrade to Edgy or Dapper.

---

### Post by mcduck on 2007-08-07
> **TruthOrDare said:**
> So basically, Ubuntu detects the PATA and uses sda for my hard disk, but grub tries to use hd0, so maybe thats the conflict that is stopping the install at 94% with a hd0 error?

Is there any work around for it?

Grub doesn't use disks the same way Linux itself does. When Grub is loaded your Kernel isn't loaded yet so what Linux kernel does has nothing to do with Grub. So the sda1/hda1 naming is not the same as Grub's hd(1,1) format which simply tells the number of disk and partition, no matter what type of disk they are.

Anyway, if you are able to finish the install apart from Grub, you could try manally installing the Grub afterwards.

---

### Post by TruthOrDare on 2007-08-07
I tried the advice on an earlier version and Ubuntu Dapper 6.06 installed perfectly.

I'd prefer the latest version, but for a first-timer I'm happy.

It saw my hdd as IDE, which I think what was causing the problem with feisty.

As for manually installing grub, I might try it, once I feel more confident. :p

---

### Post by GadgetsGuy on 2007-08-08
> **TruthOrDare said:**
> So basically, Ubuntu detects the PATA and uses sda for my hard disk, but grub tries to use hd0, so maybe thats the conflict that is stopping the install at 94% with a hd0 error?

Is there any work around for it?

I lost a whole night's sleep over this ....

The solution is when you get to the "summary" install screen, click the ADVANCED button and remove (hd0) ... then enter
```
/dev/sda1
```

Voila!!

Now my question is how can the Ubuntu developers overlook such a major problem?? 
If you are going to use the SCSI drivers now .... you must use SCSI device names!
This should have been changed way before the updates were released .. we should not have to do the troubleshooting for you guys?!?

---

### Post by ieee488 on 2007-09-30
I tried changing **(hd0)** to **/dev/sda1** and hosed up my system.

I have two PATA hard drives. The first is NTFS and has Windows 2000. The second has the various Linux distros I have been trying.

I think **(hd0)** should be changed to **/dev/sda**. Can someone confirm?

---

### Post by miki_antena on 2007-10-30
Try installing grub not on MBR (hd0), but on the root (/) partition of the system, as in some systems GRUB cannot be installed onto MBR

---

### Post by miki_antena on 2007-10-30
Man, am I stupid. I didn't look at the date... :) :lolflag:

---

### Post by philinux on 2007-10-30
I upgraded to gutsy and my HDx became SDx and wouldn't boot.

I fixed this by using UUID in fstab. Slightly different problem but grub had no problems

---

### Post by Nebutron on 2007-10-30
> **TruthOrDare said:**
> So basically, Ubuntu detects the PATA and uses sda for my hard disk, but grub tries to use hd0, so maybe thats the conflict that is stopping the install at 94% with a hd0 error?

Is there any work around for it?

I am pretty new to ubuntu and linux in general, but just successfully installed as dual boot with winxp on a SATA HD.  It also was detected as a SCSI, but with no resulting problems.  Sounds from your description like you did more of the install manually than I did.  The only thing I did different from the prompts was to indicate the percent of the drive to dedicate to ubuntu.  I would suggest trying the install again and using following more of the suggested prompts.  Good luck!

---

