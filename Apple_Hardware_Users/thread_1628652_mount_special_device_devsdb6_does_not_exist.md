---
title: "mount: special device /dev/sdb6 does not exist"
date: 2010-11-22
forum: Apple Hardware Users
---

### Post by kstaats on 2010-11-22
As an avid YDL user for many years, I have made the big switch to Ubuntu on a brand new MacBook Pro (I believe it is at least the 7-1 series). Here is what I have done, to set the stage:

a) Had the warrantied pros install a new Seagate 500GB 7200 RPM drive. Works great.

b) Installed OSX and during this process, manually created 3 partitions: 50GB for Ubuntu, 50GB for OSX, and 400GB for Data (to be shared between OSX and Ubuntu as /Data (which has worked very well under YDL for years).

c) I put the Ubuntu MacBook Pro into FireWire target (T at boot) mode and hook it up. But Nautilus on my YDL box shows OSX (/dev/sdb3) and Data (/dev/sdb4). No sign of / (/dev/sdb5) nor /home (/dev/sdb6).

d) So, at a terminal I manually mount /dev/sdb6 (as root, of course), and get this:
mount: special device /dev/sdb6 does not exist

e) I run parted on sdb and it shows all partitions:

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      211MB   4210MB  3999MB                                          
 5      4210MB  19.2GB  15.0GB  ext3                                    
 6      19.2GB  50.2GB  31.0GB  ext3                                    
 3      50.2GB  100GB   50.0GB  hfs+         OSX                        
 4      100GB   500GB   400GB   hfsx         Data   

... but when I run fdisk it sees only:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  EFI GPT
/dev/sdb2   *          26         512     3905536   82  Linux swap / Solaris
/dev/sdb3            6105       12184    48828128   af  Unknown
/dev/sdb4           12200       60785   390263076   af  Unknown

Go figure!

So, I manually edited /etc/fstab on the Ubuntu box to get rid of the UUID crap and yet, no go.

I am completely baffled.

(adding this new bit of information)

Using Disk Utility under OSX, when I select the gray'd-out partitions they are labeled as FAT-32 format (not ext3 as the Ubuntu installer says they are). But when I do the same on my old PowerPC YDL laptop, Disk Utility says they are of a UNIX format.

So, looks like there is a "new" way of formatting ext3 that is not compatible with my YDL kernel (my best guess). I am thinking of rebuilding the laptop with ext2 and seeing if that works.

Thoughts?

kai

---

### Post by srs5694 on 2010-11-23
It looks to me like your YDL kernel lacks support for the GUID Partition Table (GPT) scheme for disk partitioning that Intel-based Macs use. Your fdisk output shows three partititions (plus the 0xEE EFI GPT partition) because the disk has a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is an ugly and dangerous hack used to enable Macs to dual-boot, particularly with Windows systems.

It's not clear to me if you need regular access to the disk from YDL. If so, the best solution is to recompile its kernel to include GPT support. A lesser alternative would be to use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to rejigger the hybrid MBR to include the appropriate partitions rather than the ones that are there now. If you're just using YDL to check the disk or do a one-time data transfer, there may be other ways to do what you want with it. Post back with more details about what you're trying to accomplish to get more advice.

---

### Post by kstaats on 2010-12-10
Thank you for the reply, and my apology for the late response. I am simply trying to do what I have done for many years: target booting from one Mac to another as the fastest possible means of rsync'ing between two machines.

One machine goes into Target (firewire drive) mode and the other mounts it.

If it is a Linux kernel issue, that does not explain why OSX also sees the new Linux formatted ext3 partitions differently than it did when built under YDL.

Again, the Linux ext3 partitions on my MacBook Pro show as FAT32 under OSX, but Linux ext3 partitions on my G5 PowerMac show as UNIX under OSX. Strange.

For now, I am rsyn'ing over ethernet, which is not horrible, just requires a few more steps (checking IP addresses and booting into a fully active OS on the target, instead of just the rapid boot into Target).

kai

---

### Post by srs5694 on 2010-12-11
You should know that filesystem types can be identified in two ways. One way is to examine the filesystem itself for whatever identifying characteristics it's got. Another is to examine the partition table data on the partition. The former way is much more reliable, but many OSes rely on the latter approach, at least for a first pass at the identification.

You should also know that the Master Boot Record (MBR; the partitioning system used on most PCs), Apple Partition Map (APM; the partitioning system used on 680x0- and PowerPC-based Macs), and GUID Partition Table (GPT; the partitioning system used on Intel-based Macs and some new PCs) systems all provide different sets of partition type codes. Most notably, under GPT, most Linux filesystems, FAT, and NTFS all share a single type code. (Lame, yes, but that's the way it is.)

I suspect these two issues are the source of some of your confusion -- what you're seeing is the effect of the different ways your OSes identify filesystems in conjunction with the different partition type codes on different partition tables.

---

