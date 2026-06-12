---
title: "Help with NTFS read/write support"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by jcorden on 2007-09-14
Bit of assistance req'd. After struggling with Vista Home Basic on a brand new PC I have made the jump to Ubuntu. I have 2 hard drives in my PC, A 160GB drive that Vista was pre-installed on and a 40GB drive that I have just added. All my files, images, work etc is on the 160GB drive.

I have installed Ubuntu on the 40GB drive so I don't have to worry about partitioning disks etc and it all works just fine. 

Can someone explain in plain and simple English the stuff about FAT32 and NTFS discs. I have followed the instructions here [http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04) to install ntfs-3g to enable ntfs read/write support. Although it has worked just fine (I can read and write to my 160GB disk) I don't really understand what I have done. Will Vista still be able to read and write to this disk

I am so impressed with Ubuntu so far (its way quicker than Vista) that I will probably use it as my main operating system. Hence in the long term I will probably migrate all my files to the same disk that Ubuntu is installed on. If I do this will Vista still be able to access these files?

Is there a preferred way of setting up the two operating systems so they can share files.

---

### Post by kagashe on 2007-09-14
> **jcorden said:**
> Will Vista still be able to read and write to this disk.
yes.

---

### Post by splintercellguy on 2007-09-14
Your setup is just fine the way it is. Yes, Vista can r/w to the NTFS partition.

---

### Post by justleen on 2007-09-14
windows will still be able to read your NTFS drives..
the ntfs-3g is just a driver for linux, so i can handle ntfs writing.

for windows EXT3 read/write, install the ext2/ext3 driver
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by theDaveTheRave on 2007-09-14
Jcorden.


I can't believe the number of times that people are puting in a request for what seem like the same / similar issues!?

unfortunately reading your full post I get the feeling I'm not going to be able to adequately answer your queries.

but I followed the instruction here

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)


and everything worked fine and was reasonably explained, with regard to what was being done.

I also seem to recall having to play around with the fstab (essentially it tells the system where all the disks/partitiion are and what their  permissions are).

in a nut shell though (and this may not be highly acurate as I'm doing it from memory!).

FAT32 and NTFS are types of filing system (ubuntu / linux has the option of using other systems eg RieserFS and many others).

All file systems are set up from the start with a certain amount of disk block space for each file (this is before you even create a file and save it!).

This information is obviously stored on the disk and is the reason why your 160GB HDD never has a full 160GB available for use.

FAT32 is a File Allocation Table system, and as such allocates the blocks and stores this info as to the start and end of each block.

NTFS is (as far as I am aware, and I'm sure someone will correct me) the all singing all dancing version of FAT32 - as it allows files and directories to be shared and to have access permisions (it includes an ACL - access control list - or something like that anyway).

For both FAT and NTFS, all the space is allocated from the front to the back of the disk, when your file gets to the size of the block then it will put a tag at the end and send a marker to the next block.
This is partly why you need to "compress" and "clean" your windows file system, this process essentially puts all the bits of a single file in consectve block - for faster access and some (if limited) space saving.

On the other hand the RieserFS is a different type of filing system, again it allocates blocks at the start, but it alocates fewer larger blocks (from how I understand it anyhow). The clever bit  is that is understands where the read heads on your HDD sit when they are at rest, and starts writing to blocks in these areas first (a bit like having a spiral bound pad with tabs at the side marking of certain positions).

This means that when you want to access a file the read heads don't have so far to move to find the file.
Also as the block are larger each file is written in the middle of a block and expands to meet the outer edges (it literally writes in both directions at once - with both hands!) I don't understand how this happens but that is how I understand it!

Now the big quesion is will Vista be able to read and write to your disks, unfortunately MS OS's only support the access of FAT32, FAT64 (blocks that are double the size of those in FAT32 - which I guess is obvious from the name), and NTFS. Ubuntu and Linux / Unix systems are able to read an write a number of different file systems.

When it comes down to weather or not Vista will be able to access any data on your Ubuntu partition, the answer is unforutately going to be NO, but create a sub partition of your HDD and by having it as NTFS or FAT32 you should be able to put files there and then access them whenever you need to.

I don't know how helpfull that is, but I'm sure if I am way off base people will say something!

Dave.

One thing, I wish the that when newbies have disk problems the post I have linked too would come up at the top of the search list, it doesn't always, and I'm sure that it could be linked to the absolute beginner and /or the hardware section as this is a VERY COMMON QUERY!

Or maybee a "common problems" section should be more easily locateable?

just a thought...

Dave

maybe the forums staff will find it in their schedules to sort that one out!?

---

### Post by kagashe on 2007-09-14
> When it comes down to weather or not Vista will be able to access any data on your Ubuntu partition, the answer is unforutately going to be NO, but create a sub partition of your HDD and by having it as NTFS or FAT32 you should be able to put files there and then access them whenever you need to.
[Access Linux partitions (ext2, ext3) from Windows Vista]("http://www.go2linux.org/accessing-linux-drive-ext-with-vista")

kagashe

---

### Post by jcorden on 2007-09-14
Thanks for that:

So, am I correct in thinking:

1) With ntfs-3g installed Ubuntu can read/write to FAT32 & NTFS
2) Vista can only read/write to FAT32

When Ubuntu is installed does it set up a HDD to NTFS or FAT32 by default?

If I'm planning on using Ubuntu as my main OS should I be storing my data on the same drive that Ubuntu is installed on?

If I copy data from my Vista drive to my Ubuntu drive will I be able to read write to these files or will there be a permissions problem.

Sorry for being so dim

---

### Post by justleen on 2007-09-14
1) yes
2) NO. Windows natively supports NTFS and FAT read/write  (obviously.....)

you can choose what to drive to store your data on.... it doenst matter at all.. if you want windows to read/write to EXT3 (your unbuntu disks) install the ext3 driver for windows.

---

