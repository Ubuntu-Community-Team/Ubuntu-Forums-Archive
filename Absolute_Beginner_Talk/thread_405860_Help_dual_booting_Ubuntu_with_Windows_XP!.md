---
title: "Help dual booting Ubuntu with Windows XP!"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by ChrisUK on 2007-04-10
Hi all.

I am trying to install Ubuntu and I am having some problems with the partition's.
Basically, I would like the same setup as pictured below:
[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

Here is what my partition's look like at the moment:

/dev/sda1          FAT16          78.41MB
/dev/sda2          NTFS            86.44GB
/dev/sda3          EXTENDED    2GB
/dev/sda5          FAT32          2GB
Unallocated        Unallocated   4.64GB

The FAT16, Extended and FAT32 I believe are something to do with Dell, Mediadirect, etc.
When I treid to install Ubuntu I resized the NTFS partition to about 17GB, I then made a new partition from the unallocated space which I made into EXT3 /home for all my shared files to go, then when I tried to make the linux swap partition it said "It is not possible to create more than 4 primary partition's".

As you can see I have 4.64GB of Unallocated space, how do I get rid of that??? 
Any help would be appreciated.

---

### Post by thefoolisme on 2007-04-10
I had this problem the other day.  Delete all the ext partitions you made (leave the Windows alone).  Then create an extended partition that is the size of the unallocated space.  Once that's done, you should be able to create as many "Logical" partitions in there that you need.

---

### Post by brennydoogles on 2007-04-10
> **ChrisUK said:**
> Hi all.

I am trying to install Ubuntu and I am having some problems with the partition's.
Basically, I would like the same setup as pictured below:
[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

Here is what my partition's look like at the moment:

/dev/sda1          FAT16          78.41MB
/dev/sda2          NTFS            86.44GB
/dev/sda3          EXTENDED    2GB
/dev/sda5          FAT32          2GB
Unallocated        Unallocated   4.64GB

The FAT16, Extended and FAT32 I believe are something to do with Dell, Mediadirect, etc.
When I treid to install Ubuntu I resized the NTFS partition to about 17GB, I then made a new partition from the unallocated space which I made into EXT3 /home for all my shared files to go, then when I tried to make the linux swap partition it said "It is not possible to create more than 4 primary partition's".

As you can see I have 4.64GB of Unallocated space, how do I get rid of that??? 
Any help would be appreciated.

Looks like a pretty good setup, but I have a few questions. I noticed that you wanted your ext3 partition to be home/shared files. While dualbooting it is a great idea to set some space aside to share with windows, but you most likely don't want it to be your home partition (as xp does not natively recognize ext3 filesystems) . A better idea would be to create a smaller fat32 partition to use as shared windows/linux space, and you can even create a symbolic link to it in your home folder once you have mounted it 
```
ln -s /dev/sda*numberofthedrive* /home/*yourusername*/shared_storage
```
replacing the text between the ** with the correct information.

I also noticed that you had a pretty small looking root partition, and thought it best to advise you to allocate at least 10 gb if possible to root, because if you install alot of programs, you don't want to run out of space. Good luck with your dualboot, and welcome to the community!!

---

### Post by thefoolisme on 2007-04-10
Good point Brenny.  That's what I did - set up a FAT-32 partition to use as shared storage for both OSs.  I then actually set it up in Gparted when I installed so it was part of the filesystem i.e. /shared_storage, so I wouldn't have to worry about mounting it later.  Did the same thing with the Windows XP partition so Ubuntu could access that if I needed to as well i.e. /windows or /media/windows.

---

### Post by ChrisUK on 2007-04-10
Thanks for the replies.

I am quite new to this so I am still learning. On phychocat's tutorial on Partitioning, he says: > This last dual-boot scenario is my favorite now that I know about FS-Drive, which is a small program that allows Windows to read from and write to Ext3 partitions. So FAT32 can go out the window--one less partition to worry about and none of the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB).

That was my plan, so I could install FS-Drive on Windows which would mean I could read and write to EXT3.

I still don't understand how to get rid of the unallocated space, how do I add it to the other partition's?

---

### Post by yellowband on 2007-04-10
I'm planning on doing the same thing.
I will have two NTFS partitions (for XP and vista), then Ubuntu's ext3 partition, a swap partition, then a large ext3 partition that will be my /home directory in ubuntu as well as my shared partition for all OS's. I decided to make it ext3, like you, because of being able to install software that allows windows to read ext3 filesystems.  This avoids the limitations of using a FAT filesystem.

As for your partition woes, as far as i understand, you can only have 4 logical partitions on a disk, therefore, if you want more, you have to make the 4th an extended partition. In that extended partiton you can create as many "sub"partitions as you want.

It could look something like

hda1 = logical
hda2 = logical
hda3 = logical
hda4 = extended
       hda5 = logical (in the extended hda4)
       hda6 = logical (in the extended hda4)
       etc....

---

### Post by ChrisUK on 2007-04-10
Thanks for the reply.

I have tried to create a new extended partition in Gparted, but it will not let me. It seems to be grayed out... :confused:

EDIT: I think I have found the problem. I already have an extended partition, and apparently you cannot have two extended partition's on one drive. I will have another try in a few minutes.

EDIT2: Well I can't delete or move the Dell Extended partition, so I don't know what to do... I can't create any more primary partitions because they are all used up, Extended and Logical partitions are grayed out so I basically can't create any new partition's. What a mess!

---

### Post by ChrisUK on 2007-04-11
Hi.

I managed to do it last night after messing around with Gparted for a while and now Ubuntu is installed.
I can see my /home partition from Windows after installed FS-Drive, so it's working OK.

Thanks for the help.

---

