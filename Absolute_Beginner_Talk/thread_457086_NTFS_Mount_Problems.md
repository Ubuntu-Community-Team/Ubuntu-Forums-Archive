---
title: "NTFS Mount Problems"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-28
Hey, I got my backup NTFS mounted with some software, it's been working fine up until recently. I'm now getting this error message when I try to write to it : "Error "I/O error" while copying "/home/craig...balu (2001)"."  What can I do to fix this? I have NTFS Configuration Tool loaded and have it set to write but I'M having this error now. Any ideas??

---

### Post by Lucifiel on 2007-05-28
Do you get this error when copying large files and folders?

Perhaps you could try copying less files at one time and see if you get the error again.

---

### Post by taurus on 2007-05-28
How do you mount that ntfs partition and where do you mount it to?

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Tumpster on 2007-05-28
I get it for both small and large files....

---

### Post by Tumpster on 2007-05-29
Bump!

---

### Post by szaka on 2007-05-29
Some devices, like the Seagate FreeAgent ones, like to power down randomly. You can confirm such hardware errors from the log files. What's the output of the below line?

egrep -i 'ntfs|dma|fuse' /var/log/messages /var/log/messages.log /var/log/daemon.log

---

### Post by Tumpster on 2007-05-30
new MFT record
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Mft record 0x1029 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Could not allocate new MFT record
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Mft record 0x1029 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Could not allocate new MFT record
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Mft record 0x1029 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Could not allocate new MFT record
/v

This, all across the board........not good.....not good

---

### Post by moffa on 2007-05-30
Have you tried running chkdsk in windows as it suggested?  Seems like it a problem, either a hardware or software problem.  I would try running chkdsk and if that doesn't work, a thorough disk check using your hard driver manufacturer's utility.

---

### Post by szaka on 2007-05-30
> **Tumpster said:**
> 
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Mft record 0x1029 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!
/var/log/daemon.log:May 27 16:06:01 localhost ntfs-3g[3755]: Could not allocate new MFT record
/v

This, all across the board........not good.....not good
It's not good but it's not a tragedy. Some accounting info is stored redundantly on NTFS and ntfs-3g detects that they contradict to each other, hence it refuses to make the requested changes (and it reports I/O errors). Windows chkdsk must be able to correct this error trivially.

This error is known to happen with the Microsoft NTFS driver rarely, or if Windows or Linux wasn't shutdown properly or external storage devices weren't unmounted and detached properly.

---

### Post by Tumpster on 2007-05-31
Now I do not have a dual booting machine, I'm sole linux. Is there a good linux checkdisk I can run?

---

### Post by Tumpster on 2007-05-31
Bump!!!

---

### Post by szaka on 2007-05-31
> **Tumpster said:**
> Now I do not have a dual booting machine, I'm sole linux. Is there a good linux checkdisk I can run?
Yes, ntfs-3g upgrade, especially made for you ;-) It can be downloaded from [http://ntfs-3g.org/ntfs-3g-1.601.tgz](http://ntfs-3g.org/ntfs-3g-1.601.tgz)

Remove your current ntfs-3g package then install this release following [http://ntfs-3g.org/index.html#installation](http://ntfs-3g.org/index.html#installation)

Let us know how it worked and if you need any help.

---

### Post by Tumpster on 2007-06-03
So I did that and am still having the troubles. I get an error: "Error "I/O error" while copying "/media/backup/Pics"" for instance when I'm backin up my photos. Where can I find a scandisk to fix this?? I only have a linux box, nothing else. Any advice?  |:|

---

### Post by szaka on 2007-06-03
I think your upgrade didn't work out and you're still running an old version, or you have another problem now. What's the full output of:

egrep -i 'ntfs|dma|fuse' /var/log/messages /var/log/messages.log /var/log/daemon.log

The ntfs-3g version 1.601 was tested and reported to work for others in the same situation you have.

---

### Post by Lucifiel on 2007-06-03
I think the only utility I've found so far is : ntfsfix . But I'm not sure how safe it is to use this or how effective it is. 

[http://man.linux-ntfs.org/ntfsfix.8.html](http://man.linux-ntfs.org/ntfsfix.8.html)

---

### Post by szaka on 2007-06-03
> **Lucifiel said:**
> I think the only utility I've found so far is : ntfsfix . But I'm not sure how safe it is to use this or how effective it is. 

[http://man.linux-ntfs.org/ntfsfix.8.html](http://man.linux-ntfs.org/ntfsfix.8.html)
Well, I wrote that man page and partly ntfsfix too :-) I'm working on NTFS development  for over 5 years and lead the NTFS-3G project ;-)

I didn't mention ntfsfix because it can't fix Tumpster problem but it could cause new problems. Ntfs-3g  includes the ntfsfix code but it's safe too use and the not yet announced 1.601 release was exactly made for the problem Tumpster has.

There were 220 cases when the driver can report I/O error, what Tumpster has is only one of them. Now ntfs-3g  supports that case but there are still 219 other ones which may cause new problem. We can tell this only if the asked log is sent. But I think not the 1.601 release was used by accident.

---

### Post by Tumpster on 2007-06-03
craig@craig-desktop:~$ egrep -i 'ntfs|dma|fuse' /var/log/messages /var/log/messages.log /var/log/daemon.log
/var/log/messages:May 31 11:51:10 localhost kernel: [17179572.780000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 217
/var/log/messages:May 31 11:51:10 localhost kernel: [17179572.780000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 217
/var/log/messages:May 31 11:51:10 localhost kernel: [17179573.188000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 225
/var/log/messages:May 31 11:51:10 localhost kernel: [17179573.188000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 225
/var/log/messages:May 31 11:51:10 localhost kernel: [17179573.596000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
/var/log/messages:May 31 11:51:10 localhost kernel: [17179573.596000]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
/var/log/messages:May 31 11:51:10 localhost kernel: [17179573.596000]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
/var/log/messages:May 31 11:51:10 localhost kernel: [17179575.828000] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(133)
/var/log/messages:May 31 11:51:10 localhost kernel: [17179575.860000] hdb: 490234752 sectors (251000 MB) w/7936KiB Cache, CHS=30515/255/63, UDMA(133)
/var/log/messages:May 31 11:51:10 localhost kernel: [17179575.880000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
/var/log/messages:May 31 11:51:10 localhost kernel: [17179575.880000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
/var/log/messages:May 31 11:51:10 localhost kernel: [17179576.396000] forcedeth: using HIGHDMA
/var/log/messages:May 31 11:51:10 localhost kernel: [17179587.164000] saa7134 ALSA driver for DMA sound loaded
/var/log/messages:May 31 11:51:10 localhost kernel: [17179589.824000] fuse init (API version 7.3)
/var/log/messages:May 31 11:51:15 localhost kernel: [17179604.280000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
/var/log/messages:May 31 12:37:49 localhost kernel: [17182400.492000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 12:37:49 localhost kernel: [17182400.492000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 13:03:11 localhost kernel: [17183921.804000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 13:03:11 localhost kernel: [17183921.804000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 16:02:40 localhost kernel: [17194691.108000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 16:02:40 localhost kernel: [17194691.108000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 16:42:27 localhost kernel: [17197077.352000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 16:42:27 localhost kernel: [17197077.352000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 16:42:41 localhost kernel: [17197091.580000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 16:42:41 localhost kernel: [17197091.580000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 16:43:21 localhost kernel: [17197132.148000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 16:43:21 localhost kernel: [17197132.148000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 16:43:45 localhost kernel: [17197155.776000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 16:43:45 localhost kernel: [17197155.776000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 16:58:00 localhost kernel: [17198010.588000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 16:58:00 localhost kernel: [17198010.588000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 17:01:12 localhost kernel: [17198202.516000] hda: dma_timer_expiry: dma status == 0x60
/var/log/messages:May 31 17:01:12 localhost kernel: [17198202.516000] hda: DMA timeout retry
/var/log/messages:May 31 17:01:13 localhost kernel: [17198203.652000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 17:01:13 localhost kernel: [17198203.652000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 17:01:34 localhost kernel: [17198224.240000] hda: dma_timer_expiry: dma status == 0x60
/var/log/messages:May 31 17:01:34 localhost kernel: [17198224.240000] hda: DMA timeout retry
/var/log/messages:May 31 17:01:48 localhost kernel: [17198238.648000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 17:01:48 localhost kernel: [17198238.648000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 17:01:52 localhost kernel: [17198242.496000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 17:01:52 localhost kernel: [17198242.496000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 17:08:22 localhost kernel: [17198633.144000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:May 31 17:08:22 localhost kernel: [17198633.144000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
/var/log/messages:May 31 17:11:43 localhost kernel: [17198833.432000] hda: dma_timer_expiry: dma status == 0x60
/var/log/messages:May 31 17:11:43 localhost kernel: [17198833.432000] hda: DMA timeout retry
/var/log/messages:May 31 17:12:03 localhost kernel: [17198853.580000] hda: dma_timer_expiry: dma status == 0x61
/var/log/messages:May 31 17:12:13 localhost kernel: [17198863.580000] hda: DMA timeout error
/var/log/messages:May 31 17:12:13 localhost kernel: [17198863.580000] hda: dma timeout error: status=0xd8 { Busy }
/var/log/messages:May 31 17:12:13 localhost kernel: [17198863.580000] hdb: DMA disabled
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179573.508000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 217
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179573.508000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 217
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179573.916000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 225
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179573.916000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 225
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179574.324000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179574.324000]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179574.324000]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179576.552000] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(133)
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179576.584000] hdb: 490234752 sectors (251000 MB) w/7936KiB Cache, CHS=30515/255/63, UDMA(133)
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179576.600000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179576.604000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179577.108000] forcedeth: using HIGHDMA
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179588.648000] saa7134 ALSA driver for DMA sound loaded
/var/log/messages:Jun  3 04:46:02 localhost kernel: [17179589.388000] fuse init (API version 7.3)
/var/log/messages:Jun  3 04:46:07 localhost kernel: [17179604.492000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
grep: /var/log/messages.log: No such file or directory
/var/log/daemon.log:May 31 13:22:34 localhost ntfs-3g[3768]: Mft record 0x1029 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!
/var/log/daemon.log:May 31 13:22:34 localhost ntfs-3g[3768]: Could not allocate new MFT record
/var/log/daemon.log:Jun  1 16:54:26 localhost ntfs-3g[3768]: Mft record 0x1029 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!
/var/log/daemon.log:Jun  1 16:54:26 localhost ntfs-3g[3768]: Could not allocate new MFT record
/var/log/daemon.log:Jun  3 04:14:48 localhost ntfs-3g[3768]: Corrupt index block signature: vcn 0 inode 5
/var/log/daemon.log:Jun  3 04:14:48 localhost ntfs-3g[3768]: Corrupt index block signature: vcn 0 inode 5
/var/log/daemon.log:Jun  3 04:21:09 localhost ntfs-3g[3768]: Mft record 0x1029 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!
/var/log/daemon.log:Jun  3 04:21:09 localhost ntfs-3g[3768]: Could not allocate new MFT record


Thats my log when I run that!!

---

### Post by szaka on 2007-06-03
Ok, you're indeed still using your old ntfs-3g driver, not the new version 1.601 made for you. 

But your real problem is not that however hardware error.  There are many clear indication for that in the lines which contain {DriveStatusError BadCRC}. Make a backup urgently then replace your disk or make your hardware fixed from who you bought and if you still have guarantee.

---

### Post by Tumpster on 2007-06-12
How do I remove the old drivers and refresh with the new ones???

---

### Post by Tumpster on 2007-06-14
BUMP! Anyone willing to help me uninstall the old and install the new ones? ANy how to's or guides?

---

### Post by Tumpster on 2007-06-16
Well I got it to work, through some installation of reinstallation of the new and the old and after a reboot it mouted on boot and works just fine. No more copy errors! For now.....

---

### Post by pavan_bitsgoa on 2007-06-17
> **szaka said:**
> Yes, ntfs-3g upgrade, especially made for you ;-) It can be downloaded from [http://ntfs-3g.org/ntfs-3g-1.601.tgz](http://ntfs-3g.org/ntfs-3g-1.601.tgz)

Remove your current ntfs-3g package then install this release following [http://ntfs-3g.org/index.html#installation](http://ntfs-3g.org/index.html#installation)

Let us know how it worked and if you need any help.



this helped me a lot in solving the ntfs drives loading problem
now not only that they r recoginzed they r not write protected
thank you   szaka

---

### Post by TogusaS9 on 2007-07-04
> **szaka said:**
> Some devices, like the Seagate FreeAgent ones, like to power down randomly.

And thus cause Ubuntu to lose contact with the drive, even though it still appears mounted. I've experienced this the hard way, after running my FreeAgent Pro 750GB USB 2.0 drive under Feisty Fawn for the past few days. ](*,)

I've discovered that the FreeAgent drives do like to power down to "sleep mode", but it's not random -- the drives are set to enter sleep mode after 15 minutes as a factory default. As far as I can tell, this setting can only be changed by booting into Windows, running the FreeAgent Tools utility, and turning off sleep mode by changing the idle interval to "never".

I don't know if this "feature" can be removed by reformatting the drive for ext3, or if it can be disabled in Ubuntu without reformatting the drive -- something in Ubuntu's USB settings, maybe?

---

### Post by artanis00 on 2007-08-30
> **TogusaS9 said:**
> I don't know if this "feature" can be removed by reformatting the drive for ext3, or if it can be disabled in Ubuntu without reformatting the drive -- something in Ubuntu's USB settings, maybe?

Reformatting to ext3 does not disable sleep. I reformated my 250 almost immediately after buying it, and it still sleeps.

On a related note, it also sleeps through the auto-mount when I boot up. I can mount or pmount it after just fine, but then if it happens to not sleep though auto-mount, it mounts to SeaGate_ instead of SeaGate, since the folder those commands make don't get removed during shut-down, and auto-mount seems to not like using exiting folders.

So if someone knows how I can go about fixing that... even if it's just making auto-mount wait for the drive to wake, or have it check again, or delete the folder after everything is unmounted during shutdown...?

---

