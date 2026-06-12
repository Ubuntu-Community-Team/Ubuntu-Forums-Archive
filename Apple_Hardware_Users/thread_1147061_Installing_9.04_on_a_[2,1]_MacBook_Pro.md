---
title: "Installing 9.04 on a [2,1] MacBook Pro"
date: 2009-05-03
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2009-05-03
[FONT="Arial"]Hello,
I had Ubuntu 8.10 installed previously on this MacBook Pro.
I tried to upgrade - it did not work (I know it is not recommended) and I then proceeded to install it from CD.
It worked well for a while, but suddenly it no longer boots into Ubuntu and, to see the rEFIt menu, I need to boot holding option pushed.
If I try then to boot JJ, from within the rEFIt menu, it won't.
Here is what diskutil says:
  #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *111.8 Gi   disk0
   1:                  Apple_HFS CentralStorage          90.9 Gi    disk0s2
   2:                 Linux_Swap                         604.0 Mi   disk0s4
   3:                      Linux                         20.1 Gi    disk0s5

It looks like grub got wiped by gremlins...
I also know that there is some problem booting from disks having a number higher than 4 (Lord knows why...).
Now, the drastic solution is re-install, manually create/modify partitions as follows:

<small boot>
MacOS X (the current 90.9 GB, untouched)
Linux (say, 18 GB)
swap  (3 GB, what I have as RAM)

I would like to know whether this sounds OK first and whether there is a simpler way of grabbing again my lost Ubuntu boot...

Thank you so much.[/FONT]

---

### Post by cyberdork33 on 2009-05-03
please post the output from /Applications/Utilities/Partition Inspector (part of rEFIt).

---

### Post by GeneralSunTzu on 2009-05-04
> **cyberdork33 said:**
> please post the output from /Applications/Utilities/Partition Inspector (part of rEFIt).

Meanwhile I re-installed, and I re-partitioned the disk, without touching the Mac OS X part, so here is now diskutil output:

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *111.8 Gi   disk0
   1:                  Apple_HFS CentralStorage          90.9 Gi    disk0s2
   2:                 DOS_FAT_32 NO NAME                 195.3 Mi   disk0s3
   3:                      Linux                         14.9 Gi    disk0s5
   4:                 Linux_Swap                         2.8 Gi     disk0s6


and here is partition inspector:


*** Report for internal hard disk ***

Current GPT partition table:
 No GPT partition table present!

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1      190996785    228106934  05  Extended (CHS)
 2         409640    190988327  af  Mac OS X HFS+
 3 *           63       401624  0b  FAT32 (CHS)

MBR contents:
 Boot Code: GRUB

Partition at LBA 190996785:
 Boot Code: None
 File System: Unknown
 Listed in MBR as partition 1, type 05  Extended (CHS)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 63:
 Boot Code: Unknown, but bootable
 File System: FAT32
 Listed in MBR as partition 3, type 0b  FAT32 (CHS), active

I can now boot with rEFIt and choose which OS to boot, but I wonder whether I should synchronise the two tables (hmm the GPT does not even exist...).
Any recommendation, cyberdork?

---

### Post by cyberdork33 on 2009-05-04
I am thinking you used fdisk to partition the disk or something? Anyway... Something is wiping the GPT. I don't know what, but if it is working then don't worry about it. (You can't use the sync tool anyway as that would only blank your MBR table as well... syncing only works one way GPT -> MBR)

---

### Post by GeneralSunTzu on 2009-05-04
> **cyberdork33 said:**
> I am thinking you used fdisk to partition the disk or something? Anyway... Something is wiping the GPT. I don't know what, but if it is working then don't worry about it. (You can't use the sync tool anyway as that would only blank your MBR table as well... syncing only works one way GPT -> MBR)

Thank you.
No, I did not use fdisk, I just used a 9.04 Ubuntu installation CD to repartition the disk.
Got the feeling that the change was declaring the rEFIt partition as "rEFIt boot" and that moved  matters.
I have a feeling that there is a shortage of useful utilities, though, if one has to go though all these hoops...

Cheers,

SunZ&#301;

---

### Post by cyberdork33 on 2009-05-04
> **GeneralSunTzu said:**
> Thank you.
No, I did not use fdisk, I just used a 9.04 Ubuntu installation CD to repartition the disk.
Got the feeling that the change was declaring the rEFIt partition as "rEFIt boot" and that moved  matters.
I have a feeling that there is a shortage of useful utilities, though, if one has to go though all these hoops...

Cheers,

SunZ&#301;
gparted should be capable of making the changes and updating the GPT appropriately. I am a little confused about what all you did, but like I said, if everything is working, I wouldn't mess with it anymore.

---

### Post by GeneralSunTzu on 2009-05-04
> **cyberdork33 said:**
> gparted should be capable of making the changes and updating the GPT appropriately. I am a little confused about what all you did, but like I said, if everything is working, I wouldn't mess with it anymore.

Thank you. I won't then.
Already JJ has another significant improvement over II and that is it does not heat up the Mac as if it were a cooker!
Also, it seems to be stabler than II when you do standard stuff, and vlc works like a charm (it stuttered on intrepid).
Am therefore pretty satisfied with it so far.
If it just they would get that ATI support...

---

