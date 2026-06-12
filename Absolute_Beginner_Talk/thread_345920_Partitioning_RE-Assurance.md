---
title: "Partitioning RE-Assurance"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by FeNoM on 2007-01-24
Well, I figured out [while browsing through the forums] that creating a extended partition and then 3 logical partitions will install Ubuntu.

I have a 160 GB HD and I am planning to defragment it 3-4 times before Ubuntu install. I will then resize the HD to 100GB for the remaining windows. I will then create a 20 GIG primary FAT32 partition as a shared drive for both OS's.

Then I will use the 40GB and partition it as follows.

2GB Linux swap partition <- I chose the Linux swap option when creating. Am i right?
500MB EXT3 Partition for the Boot <- How do I assign it to be the boot partition? Is it EXT3?
37.5 GB Partition for the Root <-- Is this right?

Basically, I want to reassure myself that I am using the correct types and I want to know how I assign each partition for that it is going to do. Please check that the above is correct if not please help. I need Linux becuase I want to expand my Computer Knowledge. Once I get this set up, it will be the best thing I have done I'm sure!

PS: The 20GB partition for being shared can be primary and has to be FAT32 in order to be shared right?

A lot of questions but I'm sure someone nice enough will be able to answer!

---

### Post by drascus on 2007-01-24
Ok glad you did some research. I think you are making things a bit to hard for yourself. you don't really need to defragment windows three to four times before installing ubuntu. You can if you want but I don't really see why that is very neccisary. When you install ubuntu there will be a friendly little slider that will allow you to select how much of your hard drive you want ubuntu to run on.  When you move onto the next step the partitioner will make some space on your drive and move your windows files if need be. And partition the drive to get some space for your new OS. The it will install on this new space. When you start up your computer from then on it will ask you how you want to boot in windows or in ubuntu. Select what you want. If you need access to windows from ubuntu you can learn how to mount the windows partition later. hope this helps. 
~Drascus~

---

### Post by seshomaru samma on 2007-01-25
Sounds ok 
but why do you want a boot partition?

defrag then resize and run the Ubuntu CD
3 partitions are enough:
root (/)
home (/home)
and swap

---

### Post by Buck2348 on 2007-01-25
What he/she said (seshomaru samma).  Notice that he recommend three partitions:  /  (root), swap, and /home.  The /home might be very useful if you ever have to reinstall your system.  /home will contain all your data files, music, pictures, email, etc., and settings for the system and most applications.  it will be untouched by a reinstallation.  I would suggest 1giB for swap (if you have one gig of RAM the system will virtually never use any of the swap), 5-10 giB for root, and the rest for /home.  You would have to install most of the stuff in the software repositories to fill up 10giB with your system.  (I have only four).  It could be enlarged later if necessary.  That will leave most of the space for your stuff.

FAT32 is a perfectly good choice for a partition common to linux and windows.  Remember for later though that most any file system can be accessed by either OS.  Linux doesn't have write capability by default on NTFS, but there is an alpha or beta program that can provide it (ntfs-3g--I use it with absolutely no problems.)  Also Windows can mount ext2/3 partitions and read/write them with a small app called FS-driver.

Good luck,
Buck

---

### Post by FeNoM on 2007-01-25
> **drascus said:**
> Ok glad you did some research. I think you are making things a bit to hard for yourself. you don't really need to defragment windows three to four times before installing ubuntu. You can if you want but I don't really see why that is very neccisary. When you install ubuntu there will be a friendly little slider that will allow you to select how much of your hard drive you want ubuntu to run on.  When you move onto the next step the partitioner will make some space on your drive and move your windows files if need be. And partition the drive to get some space for your new OS. The it will install on this new space. When you start up your computer from then on it will ask you how you want to boot in windows or in ubuntu. Select what you want. If you need access to windows from ubuntu you can learn how to mount the windows partition later. hope this helps. 
~Drascus~

The problem with this is that I don't get the slider only the option to erase the entire disk or two manually partition it.

Also, I need to know what partitions I need becuase I need to create tem manually.

So far, I know now that I need a

Linux-swap partition - 2GB
Home partition - 
Root- Partition - 

What is a recommended size for the home partition and why is a boot partition not necessary. Remember that I am trying to dual-boot with windows that currently has 3 partitions. This is my I'm creating an extended partition and some 3 logical partitions. 

I need a recommended size for the three partitions, based on the fact that I will set apart 40 GIGs for the linux install, and 20GB FAT32, so 60GB will be separated in total.

---

### Post by Buck2348 on 2007-01-25
If you select manual partitioning and continue, you will have more options.  I suggest between 5 and 10 gigabytes for /(root) and the rest for /home.

Buck

---

### Post by steve.horsley on 2007-01-25
Swap - 1 to 2 gig is fine. 2G may be overkill, but won't hurt.

Root - this holds the system stuff. You need 4-5 Gig, really, depending on how many apps you instlall. Mine is 25G with 12 G used, but most of that is Unreal Tournament, UT2004 and Doom3. They're installed on the system drive rather than my home so that they are shared and anyone can use them (me and my son) and we don't need a copy each. 

Home - the rest. You can install drivers into Windows that allow it to read/write ext2/3, so you don't actually need a shared FAT drive. Not that I would want steenkin' winnders touching my Linux partitions.

If you don't make a separate boot partition, the installer uses the system partition to put the extra files on, so there's not really a need for a boot partition. that I can see.

You may want to consider creating two root system sized partitions and leaving one unused for now (I do this). Then you can install the next version on the unused partition and try it out without having to overwrite your working current install. And while you have 2 systems, you can always use one to rescue the other if you really mess one up.

As always, back everything up before starting messing with the partition table and installing a new OS. You should be OK, but you make your own luck.

---

### Post by FeNoM on 2007-01-25
Well, okay. The question that remains is that for each partition what type of partition is it.

Swap - 2GB [linux-swap]
Home - 15GB[ext3]
Root - 23GB [ext3]

If that is correct im gunna go ahead and install it.
what i want to know is how i actually set each drive. for example the swap is set up by selecting linux-swap. how would i assign home and root partitions?

---

### Post by confused57 on 2007-01-25
> **FeNoM said:**
> Well, okay. The question that remains is that for each partition what type of partition is it.

Swap - 2GB [linux-swap]
Home - 15GB[ext3]
Root - 23GB [ext3]

If that is correct im gunna go ahead and install it.
what i want to know is how i actually set each drive. for example the swap is set up by selecting linux-swap. how would i assign home and root partitions?

If it were my system, I'd set up the partitions:

Root - 10GB (ext3)
Home - 29GB (ext3)
Swap - 1GB (ext3)

You'll have to set up each as logical partitions, since you already have 3 Windows partitions(you can have only 4 primary paritions)...each of the 3 logical partitions will be within a primary Extended partition.
There should be a drop down list that you can select the mount point...root(/), home, swap  & the partitioner & installer will do the rest.

---

### Post by Tomosaur on 2007-01-25
Swap can be formatted as swap, so I'd just recommend that :P

---

### Post by FeNoM on 2007-01-25
So I will take confused advice and partition it his way. Thanks all. I will install it in a few minutes. Hopefully all goes well.

---

### Post by FeNoM on 2007-01-25
Sorry for double post, but I need to create a shared FAT32 partition for both OS. DO I set that as the 4 primary partition?

---

### Post by FeNoM on 2007-01-26
Anybody?

---

### Post by seshomaru samma on 2007-01-26
yes!


btw- if you need an urgent ubuntu assistance you can log into ubuntu's IRC channel
download xchat (they have a client for windows as well )
and log into #ubuntu 
if you havent used an IRC before dont worry , it's just like instant messeging ,but in a group. very helpful

---

### Post by seshomaru samma on 2007-01-26
yes!


btw- if you need an urgent ubuntu assistance you can log into ubuntu's IRC channel
download xchat (they have a client for windows as well )
and log into #ubuntu 
if you havent used an IRC before dont worry , it's just like instant messeging ,but in a group. very helpful

---

### Post by FeNoM on 2007-01-28
Thanks I'm familiar with IRC!

---

