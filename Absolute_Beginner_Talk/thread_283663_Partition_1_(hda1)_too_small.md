---
title: "Partition 1 (hda1) too small"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by ubuntrix on 2006-10-24
Hi there,
I would like to set up a dual boot but at the moment my Windows partition is too small (only 400 MB free space left).

As I don't think I am 'advanced' enough to manually edit the partition table when installing Ubuntu, I would like to steal some space from my other partition (with partitionmagic).

Anything I need to pay special attention to? e.g. type (NTFS, Fat32, Linux...)

Many thanks!

---

### Post by dbd on 2006-10-24
As far as I know the ubuntu partition editor is just as easy to use as partitionmagic, so I'd advise you use that. In the install just choose to "manually edit your partition table", and then you will be presented with a nice graphical interface to change your partitions.

It should be pretty straightforward to shrink your second partition and then create a few new ones for linux.

Remember, when resizing your partition there is always a risk you may lose all your data, so back it up first. Also, if you change the file system type of a partition you will lose all the data on. Also, I think it's important to defragment your partitions before resizing, so be sure to do that from windows first.

Here is some info on planning your partitions, which should cover info on filesystem type:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by louieb on 2006-10-24
Do you have one hard drive with one partition with windows installed in it?
And all that is free on that partition 400 mb.
If that is true then you have some options.
One is to compress the data on the drive and try to create more free space.
Another is to offload some data to CD or other device. OR just delete it.
Remove any unused programs.   
After that you can shrink the partition and use that to create your linux partiton and linux swap partition.
You will need about 3 gig of free space for Ubuntu.
You can go with DSL or Puppy linux they would install using the free space you have now.
And of course windows would not have any room left to add data or programs,:twisted:  .
 
If it were mine I would not mess with any of the above. To much trouble.
Check out ebay or your local mom and pop computer shop and find a second hard drive. On ebay a drive int the 10 gig range is 5 - 10 dollars. You will pay more for the shipping that the drive.

---

### Post by wieman01 on 2006-10-25
Upload a screenshot (image) of PartitionMagic if possible. This way we can tell you what's the most reasonable approach. 

I am assuming that you have made backups as highlighted by DBD. 

If you happen to have PartitionMagic, then use it to create the partition. This way you won't have to reboot all the time in case you don't have an internet connection. Loading the Live CD takes a few minutes.

---

### Post by Sef on 2006-10-25
> I would like to steal some space from my other partition (with partitionmagic).


Partition Magic and Linux often don't work well together.  Instead download [GParted]("http://gparted.sourceforge.net/").  It has GUI interface like Partition Magic.

---

### Post by wieman01 on 2006-10-25
> **Sef said:**
> Partition Magic and Linux often don't work well together.  Instead download [GParted]("http://gparted.sourceforge.net/").  It has GUI interface like Partition Magic.
Yeah, I have heard people complaining about that, but I have never had any issues with it. GParted, however, is a good option, it comes with the Live CD (Gnome Partition Editor) so there is no need to download it. Simply start the program once you have booted from Live CD.

---

### Post by ubuntrix on 2006-10-25
So far, so good.
As I am still under Windows only, I used Part.Magic.
Looks good to me, only thing that might be wrong is that the 2 partitions (swap and ext3) are "under" the light blue "extended" partition. (see attached pic.)

Do you see any problems with this? If not, I am ready to join in and install Ubuntu :D 

Thanks for the help!

---

### Post by wieman01 on 2006-10-25
The image is a bit small but I take it your **SWAP** is 1 GB in size (2 x your RAM) and **EXT3** is around 8 - 9 GB, correct?

If so that's sufficient for the time being. You could start installing Ubuntu right away. While installing Ubuntu, the system will ask you for manual partitioning. Please select that option & tell the system where your SWAP partition & root (=main) partition should go. 

If you're not sure what you ought to do during the installation, drop us a note.

---

### Post by ubuntrix on 2006-10-27
Thanks!
Everything worked out fine!

Cheers, Ubuntrix

---

