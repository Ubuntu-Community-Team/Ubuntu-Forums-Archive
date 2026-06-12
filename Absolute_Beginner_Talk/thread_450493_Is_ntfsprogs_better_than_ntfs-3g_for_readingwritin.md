---
title: "Is ntfsprogs better than ntfs-3g for reading/writing ntfs"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by evolving_monkey on 2007-05-21
Hello all,
     I have been having alot of problems with ntfs-3g. It just says that I don't have permission to write to ntfs drive. From what I am reading in the posts ntfs-3g seems to be buggy and unreliable. (just an observation not a conclusion) 

Is ntfsprogs a good addition or replacement for ntfs-3g. Or is writing to ntfs from linux just not something you can reliably do.

Are there other distros of linux that are better suited for writing to ntfs? I have played with a few but so far I have liked Ubuntu the best. It has been the easiest to work with from a "noob" stand point.  Ubuntu seems like a great introduction to linux. Also i have been impressed with the community. Much good advice from friendly folks,

Thank you for your time.

---

### Post by Terl on 2007-05-21
I think writing to ntfs is still a work in progress.  I have not had any issues yet.  I do keep backups just in case though.

I use ntfs3g myself.

---

### Post by Lucifiel on 2007-05-21
Hmmm...  is it because ntfs-3g doesn't mount the volumes properly? Do you get some message about "dirty volumes" and such?

If that's the case and if you still have WinXP, go boot into it twice and shut down the pc properly. Or run chkdsk from WinXP if you want. :) That might solve your problems with the ntfs volumes not being editable.

Also, can you open up Terminal (Applications ====> Accessories ====> Terminal) and paste this command into Terminal? And give us the output of fdisk? 
> sudo fdisk -l 

And also, could you press Alt + F2 and then paste this command into the pop-up box? And copy and paste all the contents of fstab into your post? 
> gksudo gedit /etc/fstab

Thank you! :)

---

### Post by szaka on 2007-05-21
> **evolving_monkey said:**
> I have been having alot of problems with ntfs-3g. It just says that I don't have permission to write to ntfs drive. From what I am reading in the posts ntfs-3g seems to be buggy and unreliable. (just an observation not a conclusion) 


Hi evolving_monkey. 

I'm the ntfs-3g lead developer and I'd like you to ask please describe all the problems you think are ntfs-3g ones. Our project lists all known ntfs-3g issues at [http://ntfs-3g.org/support.html](http://ntfs-3g.org/support.html) and we are not aware of any reliability problem in ntfs-3g.

Thank you in advance, Szaka

---

### Post by Terl on 2007-05-21
> **evolving_monkey said:**
> Hello all,
     I have been having alot of problems with ntfs-3g. It just says that I don't have permission to write to ntfs drive. From what I am reading in the posts ntfs-3g seems to be buggy and unreliable. (just an observation not a conclusion) 

Is ntfsprogs a good addition or replacement for ntfs-3g. Or is writing to ntfs from linux just not something you can reliably do.

Are there other distros of linux that are better suited for writing to ntfs? I have played with a few but so far I have liked Ubuntu the best. It has been the easiest to work with from a "noob" stand point.  Ubuntu seems like a great introduction to linux. Also i have been impressed with the community. Much good advice from friendly folks,

Thank you for your time.

I use the ntfs-config utility that is available via synaptic.  It is a nice little graphical way to set up the mounts.  You are given read only at first but later one of the choices is to be able to write.  I have had no problems with it.  Have you tried this utility?

---

### Post by Inxsible on 2007-05-21
> **evolving_monkey said:**
> Hello all,
I have been having alot of problems with ntfs-3g. It just says that I don't have permission to write to ntfs drive. From what I am reading in the posts ntfs-3g seems to be buggy and unreliable. (just an observation not a conclusion) 
 
Is ntfsprogs a good addition or replacement for ntfs-3g. Or is writing to ntfs from linux just not something you can reliably do.
 
Are there other distros of linux that are better suited for writing to ntfs? I have played with a few but so far I have liked Ubuntu the best. It has been the easiest to work with from a "noob" stand point. Ubuntu seems like a great introduction to linux. Also i have been impressed with the community. Much good advice from friendly folks,
 
Thank you for your time.
 
Are you sure you own the drive/folder that you are trying to write to?
 
Maybe its just a permission issue and not with ntfs-3g. To change ownership of a folder use
```

sudo chown -R <your-username> <drive or folder you want ownership of>

```
 
Also verify in Applications --> System Tools --> NTFS Configuration Tool
that both the checkboxes are 'checked'

---

### Post by eentonig on 2007-05-21
ntfs-3g works just fine for me under Feisty Fawn. But I did needed a colleague to inform me that I needed to shut down my pc properly. And don't use the Hibernate function. It's as strict as linux when it comes to mounting and unmounting. (Which actually is a good thing, but this forces me to accept the huuuuuuge XP boottimes when I come to work in the morning.).

---

### Post by evolving_monkey on 2007-05-21
Thanks you everyone for your input. I will gather the information you have requested and post back.

Szaka, thank you also for responding. I am not sure what problems are with ntfs-3g, if any. It could be good old fashioned user error on my part. When I said that ntfs-3g seems unreliable I should have said that writing to ntfs from Linux seems unreliable. I am new to Linux so it could simply be a configuration issue.  I have no facts only questions. I resized my Windows XP partition as well as the ntfs  partition I am having trouble writing to with Partition commander 10 Pro. I have read along the way that some have had trouble writing to and sometimes finding partitions that have been altered with Partition Commander. I will post back anything I think might be related to ntfs-3g   as I go along. I will probably end up loving ntfs-3g once I figure out what I am doing. 
The reason I asked about ntfsprogs is because it has Ubuntu's emblem by it. I wasn't sure if that meant they recommended it instead for compatibility reasons.

Looking forward to learning.

Thanks again for everyones time.

---

### Post by evolving_monkey on 2007-05-28
Sorry it's taken so long to respond. Cable line was cut due to construction.

There might have been a problem with the partitions after I changed things with Partition Commander 10 Pro. Windows was having trouble with the partitions as well. The windows instalation started acting really buggy.

I also began to wonder if the fact that I need to patch Windows to make it detect the true size of the hard drive (157 gigs sata) is causing a problem with Linux writing to the ntfs partion. From what I have read this is bceause the mainboard is a bit older and does not itself see over 132 gigs on a hard drive. I have not checked to see if that is editable in the bios. I wanted to do a littile more reading before I messed with that part of the bios.

Since the problem seemed to be with the partitions themselves and I was so close to the beginning I decided to reload both os's and start from scratch. I tried to recreate everything as it was when I first added Ubuntu. I could write to the ntfs partition then. Everything got wierd after using partition commander. Also, I relaized that I could write to an ntfs partition on the server with no problems (Windows 2000 Server Standard) which is really the most important part for my needs anyway. 

**I do not think that ntfs-3g has anything to do with the problem. Sorry for the confusion.** 

Windows XP Pro  is back on and I used the XP cd to set up the partitions.

I am wondering if Feisty 7.04 is as good or better than v6.06 LTS for slightly older systems. Not sure if the improvements in Feisty 7.04 might be a little over this systems head. I have a Gateway 6100 pc. 
3Ghz p4
1gig (2 x 512mb ddr) dual channel
Nvidia 5200 OEM video card (256Mb ddr)
157gig Maxtor SATA HD (7200rpm)
Intel pro 100 ethernet
SoundBlaster Audigy 2 OEM soundcard

It is a few years old but it is still pretty quick and stable for the age. 

Both versions of Ubuntu seem to detect my hardware pretty well. Both seem to install and dual boot well with Windows XP without any problems. I am new to Linux and I'm trying to figure out which would be the most stable for the system I want to put it on (described above). It is not my main work system but it is one that I do work on sometimes for convenience so I need it to be as stable as reasonably possible. Atleast until I figure out what I'm doing.

Trying to learn with least amount of caffeine fueled all nighters as possible.

Thanks for the help.

---

### Post by evolving_monkey on 2007-05-28
I decided to go with Ubuntu 7.04 Feisty. 6.06 LST could not mount the fat or ntsf partitions. I can still write to the server. Here is the info I was previously asked about.

To Lucifiel:

(01) here is the output from sudo fdisk -1
         Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


(02) Contents of fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1d84434e-6ad6-4ee9-aa69-8d53571cb600 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=81acbdd2-cc68-4082-a558-33f953410a7d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I do not get an error messages. In feisty the drives mount just fine. It simply gives me read only permission on local ntfs partition. Under properties it says that is owned by root. Below that it says read only. It is grayed out so there is no option to change it.  I tried the command sudo chown -R <your-username> <drive or folder you want ownership of>. It said that the file or folder could not be found.

---

### Post by spaceghoti on 2007-05-29
I'm sure my problem with read/writing NTFS on my system is due to user cluelessness, but searching for a cluebat to apply to myself has been largely fruitless.  I tried using the Automatix fix for read/write to NTFS disks which sort of worked, but it caused my system to ignore any other USB devices attached to my system, such as my external DVD drive and flash drive.  I had to uninstall them to get it back.

I've installed ntfs-3g manually along with libntfs-3g0 and ntfs-config.  I can manually mount my 80GB USB drive but it mounts as read-only and persists in denying access to any account except root.  If I use *chown -R <username> <path>* it reports success (and that the directories are read-only) but still denies access to the new owner.

I would really love to use this USB hard drive as an NTFS volume so it can port easily between my Windows and Linux boxes, but it seems that NTFS does not want to play nicely with any other systems in Linux.  Any assistance would be appreciated.

---

### Post by evolving_monkey on 2007-05-30
I have tried to change the permissions for ntfs partition with commands. I have even made a change temporarily to log in graphically as root. I always get the same response. "Folder is read only and permissions can not be changed". Do I need to log into windows to make a change or is this a sign of something else that might be wrong?

I am having problems changing anything owned by root no matter what I have tried. Root just won't listen to reason.

Thanks and keep it coming.

---

### Post by kelvin spratt on 2007-05-30
Download the dreaded  [www.getautomatix.com/](www.getautomatix.com/) and use their version it does a proper job of remounting the partitions and gives you full read and write permission to ntfs as well, i had similar problem as i could not download direct to ntfs partitions but now ok

---

### Post by evolving_monkey on 2007-05-30
This is odd. I can only mount the windows OS partition with read/write. The ntfs partition I want to mount doesn't show up in the ntfs config tool..

Is there a size limit on ntfs partitions for linux or ntfs-3g to be able to read/write?

---

### Post by evolving_monkey on 2007-05-31
I figured it out. When I install Ubuntu I tell it to use the largest available free space. This is perfectly fine if you first set up an extended partition to do it in. I did not set up the extended partition.. 

The problem had nothing to do with ntfs-3g or Partition Commander  10 Pro. I actually used Partition Commander 10 to set everything up.

I reloaded Ubuntu. This time I set up a 25gig extended partition. I then created a 10gig logical partition inside of that and formatted it fat32. The rest I left free.
When I installed Ubuntu i told it to install to the largest available free space. It installed to the free space left over in the extended partition (this was the only free space on the drive). This time when I installed ntfs-3g everything worked fine. I have full read/write support to the ntfs partition.  The partition showed up in the ntfs config utility and mounted easily. This also seemed to have cleared up at least some of the permission issues I was having (I haven't had time to check everything again).

Adding the 10gig partition to the extended partition in not required. I did that to have a place to swap with in case something goes wrong down the road. Also, if for any reason I want to add any room to the Ubuntu partition I have something to work with. 

I realize the manual install with the Ubuntu CD would probably have done this. I used Partition Commander because I knew how to use it. 

I hope this helps someone. I bet, however, that if I looked at the "how-to" manual again it probably explains all of this much better,  not sure though. I might have to look into that and see if i could have saved myself some grief. 

Thanks again to everyone. You put me on the right track.
Looks like I'm on my way to "learnin' me some Linux".

---

### Post by spaceghoti on 2007-05-31
> **kelvin spratt said:**
> Download the dreaded  [www.getautomatix.com/](www.getautomatix.com/) and use their version it does a proper job of remounting the partitions and gives you full read and write permission to ntfs as well, i had similar problem as i could not download direct to ntfs partitions but now okJust be warned that if you use that utility, you will be unable to mount any USB devices.  At least, that's what happened when I used it to mount my USB hard drive (formatted for NTFS so it can go between Windows and Kubuntu).

---

### Post by freebird54 on 2007-05-31
You might have had a bit less trouble if you had used the Partition Editor that comes with the install - it is pretty straighforward, and only has troubles with Vista (Vista can't stand ANYTHING other than itself resizing a partition).

Anyway - I have tried several ways to get things working, and I can't find any effective difference between running ntfs-3g on Ubuntu, or running the drivers on Win to access ext3 partitions.  Either way seems pretty reliable now.

Glad you chose Feisty - you have BOATLOADS of power for that! (check my sig) :)

---

