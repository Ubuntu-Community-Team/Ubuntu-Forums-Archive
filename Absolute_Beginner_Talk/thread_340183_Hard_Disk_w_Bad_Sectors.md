---
title: "Hard Disk w/ Bad Sectors?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Darko Beta on 2007-01-16
Hey all.  I have done a lot of in-depth reading and I'm ready to dual boot so I can begin learning Ubuntu.  However, gparted won't let me resize my windows partition because there are some "bad sectors."  Is there any way around this, or is it time for a new hard disk?

---

### Post by oilchangeguy on 2007-01-16
what version of windows are you running?

---

### Post by Darko Beta on 2007-01-16
I'm running XP Home SP2.  I just did a clean install in the hopes that it would clean up my hd enough to do the partitions.  No luck though.  I've run chkdsk /r /f about ten times.

---

### Post by oilchangeguy on 2007-01-16
go to my computer right click on the c: drive, select properties, tools, and look for something along the lines of scan disc (sorry i'm not in front of my xp machine) locate that and check the options to find and fix errors. it should prompt you to run it at next re-boot,  click ok, and then re-start the computer. if that fails it's probably time for a new hard drive.

---

### Post by Darko Beta on 2007-01-16
Thanks OCG--I'll give it a try.

---

### Post by irish_flu on 2007-01-16
Before you throw away the drive (assuming there's nothing you need on there) it wouldn't hurt to try removing all the partitions and starting fresh with newly-formatted ones (but don't use "quick format" since you have these sectors, no matter what the OS).

It might not help, but it's worth a shot.  It's likely physically going bad, but if you have the time to mess with it....

---

### Post by Darko Beta on 2007-01-16
Hmmm.  4 tiny little kb in bad sectors, as you can see below.  I have tried several ways to get around these bad sectors but no dice.  I'm thinking I'll have to go with a new hd unless anyone has some other advice.  I've been backing everything up to an external hd that I need, so I'll only be out the time it takes to get my rig set up with the new hd, + the cost of the hd.  No lost data.


[I]Checking file system on C:
The type of the file system is NTFS.

A disk check has been scheduled.
Windows will now check the disk.                         
Cleaning up minor inconsistencies on the drive.
Cleaning up 601 unused index entries from index $SII of file 0x9.
Cleaning up 601 unused index entries from index $SDH of file 0x9.
Cleaning up 601 unused security descriptors.
CHKDSK is verifying file data (stage 4 of 5)...
File data verification completed.
CHKDSK is verifying free space (stage 5 of 5)...
Free space verification is complete.

  39078080 KB total disk space.
   8578732 KB in 29350 files.
      8628 KB in 5247 indexes.
         4 KB in bad sectors.
    102676 KB in use by the system.
     65536 KB occupied by the log file.
  30388040 KB available on disk.[/I]

---

### Post by Darko Beta on 2007-01-17
Taking a look at my partition...  When I installed Windows, for some reason the ntfs partition was set up 7mbs short of the full disk (I sort of recall noticing this during installation, and being too lazy to correct it b/c I didn't think it would be a big deal)--so there is the ntfs partition and then 7mb of unpartitioned space.

Could this cause the "bad sectors" problem?  If it is *likely* then I may try another fresh install of Windows, but not really looking forward to it because I'll also need to do a new install if I end up needing a new hd.

---

### Post by vmikalinis on 2007-01-17
Hi,
The unpartitioned space wouldn't be the cause of your bad sectors, but it does look like you do have the signs of a failing hard disk.  If it is possible, I would image the drive with something such as syamntec ghost and drop it onto a new drive.  You could try reformatting the drive and using it, but if it does have a physical problem you will see some symptoms pop up shortly again.  I would forget about installing ubuntu for now and just try to track down the source of the bad sectors.  If it is a laptop, I have seen many drives fail due to heat and vibration, it is less common is desktops but does happen (more and more lately it seems).

---

