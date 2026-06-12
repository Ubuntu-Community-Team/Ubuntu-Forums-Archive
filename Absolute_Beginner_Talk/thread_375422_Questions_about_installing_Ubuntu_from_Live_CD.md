---
title: "Questions about installing Ubuntu from Live CD"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-03-03
Howdy!  I'm an absolute beginner at Ubuntu and have some questions regarding the installation process.  I've followed along with the GraphicalInstall walkthrough but I still don't understand what to do once I get to step 5: select a disk.

My current harddrive is divided into two partitions, c: and f:.  I have Windows XP installed on c:.  Which option should I select in order to install ubuntu?

1) Resize IDE1 Master, partition #5 (hda5) and use freed space

2) Erase entire disk (well, I don't think its that one, anyway)

3) Use largest continuous free space, or

4) Manually edit partition table?

I'm afraid I don't really understand any of those options, aside from 2.

+

If choose option 4, can anyone out there help me edit the table correctly?

Thanks in advance for any help or advice!

---

### Post by Bachstelze on 2007-03-03
Option one will resize your first logical partition (most likely the one Windows calls F:) and install Ubuntu in the free space created.

Option two will erase the whole disk and une it all for Ubuntu.

Option three will use the largest free space it can find for Ubuntu. Mind that "free space" here means "diskspace not allocated to any partition", not "space allocated to a partition but unused".

Option four will let you partition however you like, it is usually the best choice. If you want us to help you about it, you'll have to provide a bit more info (size of the drive, size and use of the existing partiton, size and use you'd like for your Ubuntu, etc.)

---

### Post by K.Mandla on 2007-03-03
Hi. Assuming you want to keep Windows, you should use option 3. That would prompt Ubuntu to find the largest empty space and use that as its installation area.

But your questions begs another question: When you say you have an F: partition, does that mean it's empty and you want Ubuntu there, or does that mean you have a second partition with data on it?

If you want to use option 3, you need to keep the area *unpartitioned* that you plan to give to Ubuntu. If it is already partitioned, Ubuntu will think it's being used and will ignore it.

You can unpartition that space by booting into XP again, right-clicking on My Computer, selecting Manage and then Disk Management, and then delete the extra partition through that dialogue.

---

### Post by Mr. Svinlesha on 2007-03-03
Thanks, Hymn!

I'd like to go with the last option, if you have the time and patience to help me work through it.

I have ~160GD of HD space, divided into two partitions: C has 78 gigs, and F has 70.  F is basically empty except for a couple of backup files.  I'm going to move them over to C as a first step.  C: has Windows and basically all of my other stuff, around 40 gigs.

I don't know how much space to use for Ubuntu: as much as it needs, I guess.

I'll go ahead and start the installation.  If you need to know anything else, ask.

---

### Post by Mr. Svinlesha on 2007-03-03
> If you want to use option 3, you need to keep the area unpartitioned that you plan to give to Ubuntu. If it is already partitioned, Ubuntu will think it's being used and will ignore it.

You can unpartition that space by booting into XP again, right-clicking on My Computer, selecting Manage and then Disk Management, and then delete the extra partition through that dialogue.You see, for me the instructions on the walkthrough are a little unclear, and I suspected that I'd have to do something like that, which is why I was afraid of just clicking on option 1 and hoping for the best.

---

### Post by Mr. Svinlesha on 2007-03-03
So...do I need to delete the F partion first, or can I just restart the installation process and go through option 4 to create/resize my already existing partition?

---

### Post by Bachstelze on 2007-03-03
If the partition you call F: - mind drive letters are not used in UNIX-like systems - is unused and you want to delete it, ou can go with option 4. It will start GParted which is a very intuitive partitioning tool. Then you can delete the partition and create partitions for Ubuntu instead. Another option would be tu run GParted manually (It's somewhere in the menus) and delete the partition, then run the instaler and choose option three.

---

### Post by proalan on 2007-03-03
I highly recommend you don't erase disk if this is your first attempt at ubuntu,
instead set up a dual boot system so that you can fall back on windows incase something goes wrong

I'd recommend a minimun 10GB of harddrive space to install ubuntu

you can either choose to resize your windows (c:) partition to free up the space or use your existing partition (f:) if there is enough space.

You'll need to create a logical partition from the remaining space after resizing windows (if you choose to do it this way)

- then you'll need to create an 'ext3' partition set the mount as '/' (root) this is where the main OS will be installed. I recommend 5GB minimum.

- then create a 'linux swap' partition, and set the mount as 'linux swap', this is similar to windows virtual memory in windows, set this in the region of 600MB - 1GB.

- then with the remaining space, create another 'ext3' partition and set mount as '/home' that will be where you store your documents (kind of like 'My Documents' in windows). The size of this partition is at your discretion and is used primarily as storage space and profile settings 

ubuntu should detect and automount your existing windows partition, so that you can access your windows files. This is mounted as '/media/hda1/' by default.

Ubuntu will automatically install a nice little GRUB loader that will allow you to choose whether to start up ubuntu or windows at system boot.

---

### Post by Mr. Svinlesha on 2007-03-03
Oh no.  proalan, could we try that again in English?

:) 

Perhaps we could start with a few simple definitions.  What is an "IDE1 Master", what is "partition #5 (hda5)," and what happens when I resize a partition?

I'd like to use F: if I can, and I've basically cleaned it out.  So I'm at step 5, and I've chosen option 4.  A kind of "pop-up" window (gparted) is showing me a graphical version of my partitions and asking me to prepare my partitions.  On the left side I have a block labeled /dev/hda1; it's 78 gigs in size, and about half of it is colored light brown: I assume that's the amount of space being used.  That ought to correspond to C:, nes pas?  

On the right side I have a block labeled /dev/hda5.  It's mostly empty.  That's F, yes?

Then, underneath, I have a list:

/dev/hda1
/dev/hda2  (with an underdirectory, i.e, a little arrow pointing down to)
/dev/hda5


the last has about 2 gigs of scrap on it, waiting to be overwritten.

What next?

---

### Post by Bachstelze on 2007-03-03
Then, if you indeed want to delete it, right click on /dev/hda5 and choose Delete. Then you'll have plenty of free space to install Ubuntu in.

As was said earlier, you need at least three partitions for Ubuntu. One for the system files, one for your personnal files and settings and one for "swap" (equivalent of Windows' virtual memory)

---

### Post by Mr. Svinlesha on 2007-03-03
I note at the top of gparted there are two buttons: one allows me to delete a partition, and the other allows me to resize it.  I can mark /dev/hda5 and resize at need.  How big should I make it, and what happens to the unpartitioned space I leave on the disk?

---

### Post by Bachstelze on 2007-03-03
The unpartitioned space is precisely where you will create partitions for Ubuntu :)

---

### Post by Mr. Svinlesha on 2007-03-03
Okay, I've deleted it.  Now I need to create 3 new partitions?

---

### Post by Mr. Svinlesha on 2007-03-03
Okay, uh, 3 partitions.  How large should they be in MiB ?  

I have several different boxes here.  Free space preceeding, New size, Free space following, (all measured in MiB?) logical partition (only option), file system (ext3?),  and also "round to cylinders" is checked by default.

What now?

---

### Post by Bachstelze on 2007-03-03
Yes, you need to create them as follows :

The root partition ("/") is the one where all the system files will go, 5 GB is usually enough but you can give it a couple more to be really safe.

The swap partition should in theory be twice your RAM but if you have much RAM, you can make it smaller - for example I have 2 GB of RAM on my laptop and my 512 MB of swap are almost never used.

The /home partition is the one where all your personnal files and settings will go, give it all the remaining space :)


About filesystems, the "standard" Linux filesystem is ext3 but I personnally use reiserfs instead. If you want to be able to access your Ubuntu partitions from Windows, go with ext3, if not, you can go with either one, you won't see much difference anyway.

---

### Post by Mr. Svinlesha on 2007-03-03
Partition 1, for my root catalogue, is 9.77 gigs.  I've got the space.

Interestingly, I'm doing this because I just lost some RAM.  It's a long story, but to make it short, a friend gave me the live CD to run a memory test.  So now I have 512 RAM, but am going to buy another 512 soonest.  So, according to your formula, 2 gigs?

And then the last partition takes the rest of the disk.  Gotcha.

Hymm, thanks so much for taking out the time to help me with this.

---

### Post by Mr. Svinlesha on 2007-03-03
Prepare mount points:

/ goes to partition 5, with 10 gigs

swap goes to partition 6, with 2 gigs

but what option do I select for partition 7?

---

### Post by Bachstelze on 2007-03-03
What "option" are you talking about ? Just create the partition, give it all the free space, set /home as mount point, that's all you need :)

---

### Post by Mr. Svinlesha on 2007-03-03
Yes, "/home."  That was the option.

God, are you in France?  I just noticed.  It's 3 in the morning here.

I'm in Gothenburg, Sweden, by the way.

---

### Post by proalan on 2007-03-03
> What is an "IDE1 Master" 
This is usually the your IDE (aka PATA) harddrive. 

> what is "partition #5 (hda5)
think of hda1, hda2, hda3 ... as the equivalent of labelling C:\ and F:\ in windows 
where hda is your harddrive and the numbers refer to partions

forget about drive letters, the file system works differently in linux, pathnames start from root '/' rather than the drive letters your used to with windows e.g. c:\windows, f:\windows etc...  


Perhaps if I give my setup it might help

/dev/hda1  (ntfs)  this contains my windows xp   (20GB)  mounted as /media/hda1
/dev/hda2  (linux-swap)                                    (1GB)    swap
/dev/hda3  (ext3)  ubuntu is installed here          (30GB)  mounted as /
/dev/hda4  (ext3)  home folder                          (10GB)  mounted as /home

your partition numbers may differ from mine, just be sure to uncheck the reformat tickbox for your ntfs, thats where your windows installation resides

---

### Post by Mr. Svinlesha on 2007-03-03
Well, I'm installing now.  Let's keep our fingers crossed.

---

### Post by Mr. Svinlesha on 2007-03-03
Well, here we are then.  I'm writing to ya from Ubuntu.  Seems to have worked without a hitch.

Thanks again for all the help.

---

