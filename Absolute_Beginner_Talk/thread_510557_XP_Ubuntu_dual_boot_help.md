---
title: "XP Ubuntu dual boot help"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2007-07-26
Hi,

So I've been attempting to dual boot XP and Ubuntu, following various tutorials that have not yet been successful.

I've tried the following steps:

[LIST=1]
[*]XP Master Drive, Ubuntu Slave Drive, no other configuration
[*]Unplug XP drive, install Ubuntu on slave drive, replug Ubuntu slave drive
[*]XP Master Drive, Ubuntu Slave Drive, instructing Ubuntu to put GRUB onto the Master
[*]Partition master drive with firs partition NTFS and XP, second partition Fat32 and Ubuntu, use slave drive for storage
[/LIST]

All of these attempts have resulted in XP being unable to boot. I suspect at least some of it has been due to Ubuntu being unable to boot, as well, but I can't verify that. Fixmbr has never worked, bootcfg has never worked, and the GRUB CD hasn't worked. Formatting both drives again and reinstalling Windows has been the only thing thus far that has resulted in a boot of anything. With the GBUB CD, I've tried all the various options that are under GNU/Linux in an attempt to boot Ubuntu after it has been installed. GRUB does recognize that Ubuntu is present, but it is always unable to boot it or create the MBR.

When running the Ubuntu installer, it once gave me an error related to creating the user, and then it appeared to continue installing, but didn't work. Other times, it has gone through the install process, and then appeared to finish. It didn't ask me to reboot, though.

Does anyone have recommendations for something that can help, and that can hopefull avoid having to format the working Windows drive again? I've run the Ubuntu CD through the disk checker on the startup screen, and it apparently doesn't have any errors.

Oh, I don't have a floppy drive at this time, if that's relevant at all.

Thanks for any help.
Jon

---

### Post by xelapond on 2007-07-26
[INDENT]I've tried the following steps:

   1. XP Master Drive, Ubuntu Slave Drive, no other configuration
   2. Unplug XP drive, install Ubuntu on slave drive, replug Ubuntu slave drive
   3. XP Master Drive, Ubuntu Slave Drive, instructing Ubuntu to put GRUB onto the Master
   4. Partition master drive with firs partition NTFS and XP, second partition Fat32 and Ubuntu, use slave drive for storage
[/INDENT]

I assume you are using two internal drives?

---

### Post by flamingsole on 2007-07-26
> **xelapond said:**
> 

I assume you are using two internal drives?

Yes, sorry about that. Should have added that. The Master is a 250 GB IDE drive, and the Slave is a 200 GB SCSI drive. There is one gig of RAM, and a 64 bit AMD Athlon processor.

Thanks.
Jon

---

### Post by charlier653 on 2007-07-26
I just reinstalled Dapper on my XP box a few days ago, after a year long hiatus from Ubuntu.

I didn't have to unplug any drives for the install to go through as a dual boot.

During the install, I was asked which drive I wanted Ubuntu to be installed on, and after the initial reformatting of that drive, grub looked for any other OS and made it's own changes before completing the Ubuntu install.

BTW: winXP is on my IDE1, and Linux on IDE2, with SATA as common file storage.


Point I'm trying to make is that the options should be there during install from a LIVE cd.

Try that, its what someone suggested to me ages ago.

---

### Post by flamingsole on 2007-07-26
That was my original attempt. In the drive selection, I told Ubuntu to use the entirety of the slave drive, being the SCSI drive. It didn't seem to like this, as it just booted back into Windows. It didn't ever realize that Ubuntu was present, although there didn't appear to be any errors in the installation.

That's when I tried the Advanced option, and I created a small FAT32 partition on the Master drive and asked Ubuntu to stick boot on that partition. That didn't work either. Windows didn't boot at all, at that point, and GRUB didn't offer any help.

Thanks.
Jon

---

### Post by kyphi on 2007-07-26
There are some problems when you try to mix IDE with SCSI drives.  To find out how to overcome these problems you may have to google for an answer.

You would have a better chance of success if you partition your IDE (master) drive and install XP first and then Ubuntu.  No need to create a separate partition for the master boot record.

If you already have XP installed on your IDE drive you can still install Ubuntu on the same drive since Ubuntu can  make a partition for itself during the install.  This partitioning can also be done by you before installing Ubuntu.

The disadvantage of putting both operating systems on one drive is that in the case of drive failure you will have lost both systems.

My recommended solution is to replace the SCSI drive with either IDE or SATA and install Ubuntu on the whole drive.

---

### Post by MQMike on 2007-07-26
The SCSI is seen the same as a SATA.
Best:  Two SATA's
Next best: Two IDEs
Perplexing at times for booting:  Any mixture thereof.

---

