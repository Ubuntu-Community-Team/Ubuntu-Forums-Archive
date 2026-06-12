---
title: "messed up hdd's - any chance i can save data ?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by slpr2000 on 2008-02-25
running ubuntu live session 7.10 32 bit

sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x929d6b21

Device Boot Start End Blocks Id System
/dev/sda1 * 1 638 5124703+ b W95 FAT32
/dev/sda2 639 7301 53520547+ f W95 Ext'd (LBA)
/dev/sda5 639 7301 53520516 b W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48a6632a

Device Boot Start End Blocks Id System
/dev/sdb1 1 19457 156288321 7 HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e696269 


GNU Parted 1.7.1

(parted) p

Disk /dev/sda: 60.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 5248MB 5248MB primary boot
2 5248MB 60.1GB 54.8GB extended lba
5 5248MB 60.1GB 54.8GB logical fat32


that is the messsed up one internal hdd, it's a notebook, the 2 drives a 160 GB are on fire wire
what happened ?
w2k on the primary, with temp and and swap on the secondary dies, loosing swap over few minutes - it just died, 
the second partion was mounted, but ubuntu freezes when i try to copy files to externals
i'd like to save some data from the 54.8GB logical fat32 drive, before i install ubuntu on the whole disk, 
the external drives are pretty full, and ntfs ;/ but thats another problem, - i may buy another drive and copy all that stuff to the new one, ...

---

### Post by Presto123 on 2008-02-25
**Edit**Blah, I misread.

---

### Post by rbc on 2008-02-25
If this sounds nasty, it's not meant to be, but i'm a bit confused as to what the actual problem is. You are running the Live CD, trying to mount partitions, and copy files from one partition to another? Just a shot in the dark, but how much memory do you have? If you are running the Live CD with less than adequate RAM, that may be why it is freezing up.

---

### Post by slpr2000 on 2008-02-26
@ rbc and your 'it sounds nasty...'  
rofl and nevermind :)

i knew i was posting not enough data about my system :P it's never enough
 
allright, hardware is a dell 8000 notebook with a p3 @ 900 mHz and 512 MB ram

it's a long time since i have been working with gdisk.exe on daily basis (assembling notebooks) but that was in-win95/98/nt times ...

i just don't want to give up and format the built in hdd

it's messed up ..noticed the two b-labelled partitions ? on dev/sda ?

- so far my thoughts were :
- buy another external drive for firewire, to backup data from the 2 x 160 GB and the 
messed up first drive's partion 

questions here are : can i change from ntfs to ext3 ( or whatever linux format ) on the fly      ? without loosing data ?

another point would be, install minimal ubuntu on those 5 GB 

question here is how do i prepare the disk without messing it up more then it already is ..

---

### Post by rickycodie on 2008-02-26
the external drive sound like the best thing to do, i reccomend using the ULTIMATE BOOT CD. it freaking rocks. it has copy and then wipe options, which sounds like what you want.

btw, no you can't switch from ntfs to ext3 on the fly. just not possible yet.

---

### Post by MasterAlone on 2008-02-26
From what I read, you are dealing with 3 different files systems, Fat 32, NTFS, and whatever the flavor is for linux.

Since NTFS can read a FAT 32, if you have the space on ecternal, copy from the itnernal to the external using win2k instead of ubuntu.  If you have a partitioner that works with NTFS and FAT32, see if you can repartition the external in a size capable of holding all that you want to copy in a FAT32 format.  Then you can install Ubunto onto the internal and it will be able to read the FAT32 portion of external.

Hope this makes sense.

---

### Post by slpr2000 on 2008-02-26
@ master alone - then you are reading it wrong, here :

internal HDD - the messed up one, which i can acces ( copied one folder but then i froze )

sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x929d6b21

Device Boot Start End Blocks Id System
/dev/sda1 * 1 638 5124703+ b W95 FAT32
/dev/sda2 639 7301 53520547+ f W95 Ext'd (LBA)
/dev/sda5 639 7301 53520516 b W95 FAT32

and the 2 160 GB which are in mobile enclosures via fire wire 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
Disk /dev/sdc: 160.0 GB, 160041885696 bytes

what i try to do is access the 
/dev/sda5 ( i can mount it ) but copying files freezes me 
on sda (build in hdd) to copy files to the externals 
so, i could wipe the disk ( the internal and install ubuntu ) 
but first i'd like to save files ...i know i know ..backups - if i had those i would not ask for help eh ? :)
OR ..
partition the internal drive by hand from live sys, the first free 5 GB and install, for now, ubuntu there, then try to copy files to those external drives, but i am afraid i will mess up the internal HDD completely 

what happened in first place ? 
on internal harddrive :
first partition was windows2000
second partition was swap and windows temp
swap dies, few minutes later windows dies too
i could boot up few times in windows but it was horrible slowly, 
now booting from hdd's is not possible = messed up parittion tables 
for now i just sit and think ...
when i try to install win again for the purpose of saving data, what will that do with my data i try to save :)
too bad i don't know enough about treating partitions to solve the problem myself

---

### Post by oedha on 2008-02-26
did you still have free space on sda5 ?
if yes....why dont you resize it and make it as linux partition ans swap.....
you will copy faster instead of using live cd........
you can resize the partition using gparted :==> [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by MasterAlone on 2008-02-26
ok, if I understand this correctly, you want to copy from a FAT32 drive to an NTFS drive using ubuntu.

According to what I've read, ubuntu can't work with NTFS.  However, that being said, I do have access to My Documents in XP using Ubuntu.  The problem may be that you are tryiing to Write to NTFS where ubuntu only have a limited ability to READ NTFS.

I have a crazy solution if the hardware is still available.  I purchased an adaptor kit for about $20 plus shipping that allows you to take 2.5" internal hd from a laptop and put it in a desktop.  If they are still available, unless this has to be overnight, get one and put the drive in computer that will see it as the second or D: drive.  Copy and compress your files to a CD.

After doing that, do it again to make sure you have a valid working copy of the files.  Put the drive back into the laptop, do a clean install of Ubuntu, then copy the files from the CD to whichever drive you want to keep them on.

I suspect tho that as long as the externals are NTFS, you may have continuing problems using Ubuntu with them.

Forgot to say I got the adaptor kit on Ebay.

---

### Post by oedha on 2008-02-26
> **MasterAlone said:**
> 
According to what I've read, ubuntu can't work with NTFS.  However, that being said, I do have access to My Documents in XP using Ubuntu.  The problem may be that you are tryiing to Write to NTFS where ubuntu only have a limited ability to READ NTFS.


ntfs can be read/written flawlessly in gutsy
i put my files on a NTFS partition which use together by win and ubuntu 
maybe you didnt set the ntfs-3g to write your disk...:)

---

### Post by MasterAlone on 2008-02-26
> **oedha said:**
> ntfs can be read/written flawlessly in gutsy
i put my files on a NTFS partition which use together by win and ubuntu 
maybe you didnt set the ntfs-3g to write your disk...:)

I am new to Ubuntu also, however I do have a number of years experience working in IT.  Among the things I have learned is that the more variables you introduce, the greater the chance of failure.  In this case, Three different file systems being read/written to by 2 or more different operating systems.

If I have made an incorrect statement about writing to NTFS, then I stand corrected, I haven't tried writing to the NTFS drive I have in my computer.  It was an assumption based on the current problem.

That said, the issue here, to me, is the ability to retrieve the data from the hard drive that is having a problem, then installing Ubuntu.  My experience has been that when there is a hard drive issue, if at all possbie, you use an operating system that is best suited for the file system that was created on that hard drive.  In this case, it could even be a copy of WIN ME or WIN 98 since they are both FAT32 based.  It's sort of like taking your pregnant wife to a proctologist instead of an obstetrician.  They're both doctors, but do things differently.

---

### Post by slpr2000 on 2008-02-26
i can write to those external ntfs 
i was able to copy one folder from the 
/dev/sda5 639 7301 53520516 b W95 FAT32
to one of those externals ntfs 
but i have trouble accessing the /dev/sda5.. it has a +b flag 
my partition table is gone to hell 
i could start resizing and try to install an OS but there is the risk of loosing access to /dev/sda5 (where the data is) i want to save
what i need is a wizard who knows w2k paritions and how to flag them right, so i can access 
/dev/sda5 somehow ..which is extended partition formatted with fat32
currently i seem to have on the internal 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 638 5124703+ b W95 FAT32  - btw gparted says no formatting here 
/dev/sda2 639 7301 53520547+ f W95 Ext'd (LBA)
/dev/sda5 639 7301 53520516 b W95 FAT32  - b flag ? that just can't be right

---

