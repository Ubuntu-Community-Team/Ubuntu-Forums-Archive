---
title: "cant  read windows disk"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by retep57 on 2006-09-19
error: device /dev/hdb1 is not removable

error: could not execute pmount

  windows system crashed, hmm  migth be good time to go ubuntu, however i need to access  some wondows files on  some harddisks in this computer, i unstalled ubuntu on an ext usb hdd, working nicely   , as in   i amusing it to write this etc,  but  i get that error msg when i try to retrieve  files  off my  sad windows  hdd,  ubuntu can see the disks but  cant :mount:

help please

---

### Post by PietreWitobi on 2006-09-19
I am reasonably sure that the Filesystems are incompatible, as Windows (XP atleast)  Uses an NTFS system, and Ubuntu uses "Extended 3"  I think both can read FAT32, but that's as far as the overlap goes.

I hate to say it, but I think you might have to cut your losses - unless you want to install Windows on that USB hdd of yours and try to access it that way.  (I have no idea if that will even work.)

---

### Post by nudnik on 2006-09-19
I beleive there is a way to get Ubuntu to read some of the files, but you will need one of the gurus to assist you in that regard.

 If that fails, you can retrieve them via DOS, or by connecting another hard drive with Windows installed and optimised for that machine. Instruct the BIOS to boot from the new disk first, and then use the pristine OS to retrieve your data from the corrupted one.

---

### Post by retep57 on 2006-09-19
> **PietreWitobi said:**
> I am reasonably sure that the Filesystems are incompatible, as Windows (XP atleast)  Uses an NTFS system, and Ubuntu uses "Extended 3"  I think both can read FAT32, but that's as far as the overlap goes.

I hate to say it, but I think you might have to cut your losses - unless you want to install Windows on that USB hdd of yours and try to access it that way.  (I have no idea if that will even work.)

thanx anyway, i have another computer availalbe so will  remove  hd from this one and try to salvage files, am keen to  persist with ubuntu as an exercise, if i can get enuf stuff running might even stay with it, ws  just planning oon using it for emergency rescue if possible,  darn that partition majic, messed up bigtime, maybe i  clicked move/change/delyte  vital partition, dunno  ces't la vie

---

### Post by gn2 on 2006-09-19
Have you tried putting the Windows hard drives in an external enclosure?

File system incompatibilities are a problem for writing, I have found that I can easily read files on NTFS partitions when they are in my RaidSonic IcyBox, and copy them onto ext2/ext3 partitions.

---

### Post by retep57 on 2006-09-19
> **gn2 said:**
> ...can easily read files on NTFS partitions when they are in my RaidSonic IcyBox, and copy them onto ext2/ext3 partitions.
 hmm intersting thought,  dont have ext  enclosure though, thanx for idea though

---

### Post by Brunellus on 2006-09-19
to mount windows ntfs partitions follow these directions

[https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29](https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29)

note that mounting NTFS partitions should be READ-ONLY.  ntfs writing is experimental in the Linux kernel, and should not be attempted if you are not prepared to accept IRREPARABLE FILESYSTEM CORRUPTION.

---

### Post by mokmoki on 2006-09-19
you may also want to try [this]("http://www.psychocats.net/ubuntu/mountwindows") to mount your windows partition and access some files. and as the brunellus said, ntfs writing is still not fully functional, so i suggest that you don't try it...

---

### Post by Frak on 2006-09-19
Go to help and how to mount windows partitions
Its fully explained there

---

### Post by retep57 on 2006-09-20
get part way there, but  dont have  permssions, arghh, how can i not have permissons on my own computer  ..  :(  , oh yes went to the help page, way to complex for total newbie me, got stuck at the permissions   bit

---

### Post by retep57 on 2006-09-20
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffff98e8 of partition table 5 will be corrected by w(rit e)

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6608    53078728+   7  HPFS/NTFS
/dev/hda2            3149       24321   170072122+   f  W95 Ext'd (LBA)
/dev/hda5   ?      110043      216897   858305321+  fd  Linux raid autodetect

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3421    27479151   83  Linux
/dev/sda2            6847        7296     3614625    5  Extended
/dev/sda3   *        3422        6846    27511312+  83  Linux
/dev/sda5            6997        7296     2409718+  82  Linux swap / Solaris
/dev/sda6            6847        6996     1204812   82  Linux swap / Solaris
  i get this far,  but  fall over at permissions stage,, hmm will play a bit more but will have to use another xp machine to sort it out i think  , ces't la vie, good learning exercise though  ,, thanx

---

### Post by niteblind on 2006-09-20
I had the same problem last night. I can see the NTFS partition (on my usb harddrive) but it is read only even though other NTFS partitions on my network are read-write so it does not make any sense.

niteblind

---

### Post by apkolev on 2006-09-20
Hi!

I had the same problem with mounting the NTFS partitions in Ubuntu. I have Ubuntu installed on a separate drive (hdc). When I go to "Computer" I can see the other drives (hda and hdb) with all the partitions but I cannot open them. It gives the same error all over again that the volume cannot be mounted. What I did was to create directories in /media which I could assign the volumes as mount points. Then I run: *sudo disks-admin*. This allowed me to mount the partitions that i wanted by pressing the "Enable" button, after choosing the previously created directory in /media as mount point. The content of the drive is available for reading at the /mount/partition_name directory. 

The only problem is that I have to run *sudo nautilus* to view the files as by default the access is for *root* only. I can copy files or even execute them but only with root privileges. When I go back to my usual user I cannot view the contents of the drives. 

Does anyone know how to fix this permissions problem? I tried to change the permissions of a copied folder for example but it does not change the permissions of all the files that are inside. Imagine a folder with 100 files... changing them one by one is not reasonable.

I don't know if this info can help but it is just an experience that I had.

Cheers!

---

### Post by gn2 on 2006-09-20
It should be possible to mount NTFS drives in such a way that all users can access them, mount and unmount them. PCLinuxOS does it, (using GUI) so Ubuntu should too? (using terminal)

---

### Post by apkolev on 2006-09-20
Hi!

I saw this in another post and I tried it. Works 100% with all my disks and volumes. The partitions are available after restart and acessible to all users. Depending on the partition type NTFS/FAT you can have read only or write access as well. Check this out [http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows")

I hope it will help you.

Cheers!

---

