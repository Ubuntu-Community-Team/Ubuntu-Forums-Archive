---
title: "Help Setting Up Dual Boot iBook G4 w/ Panter"
date: 2005-03-06
forum: Apple PPC Users
---

### Post by ibookg4 on 2005-03-06
I was able to get Ubuntu installed on my iBook G4 800.  I choose to repartition my hard drive thus deleting my Panther install.  I would like to repeat this process, but this time set up my hard drive to allow me to dual boot.  I'm a linux newbe and I'm not quite sure how to accomplish this.

Should I first boot off of my Panter install disk, run Disk Utility and then partition?  If so, how should I accomplish this?  Should I instead use Ubuntu's partition program...it was rather difficult to understand during setup.

Thanks.

---

### Post by godsunderstudy on 2005-03-06
Boot (hold down the c key on restart) from the disk you got with your iBook (I'm not sure if the Panther disk has Disk Utility). Then go to the menu at the top and choose Disk Utility. Click on your computers icon in the left hand box, it's the first one. Click on the "Partition" tab at the top, and you should set up 4 partitions as follows:

150 meg bootstrap         Free Space
x gigs      main Ubuntu Partition (where you put the system and all the files you download. Choose size yourself)           Free Space
520 meg swap space           Free Space
x gigs  (OS X partition)       HFS+

It is important that they go in this order, if I remember correctly. Name the OS X one. Then install OS X again on your OS X partition.
Next, boot from the Ubuntu cd and go through normall until you get to the partition screen. *IMPORTANT* Choose "Manually edit partition table". You'll get a list of your partitions, select your bootstrap one, then select "Format this partition as..." and choose "New World boot partition". Next, select the swap and use it as swap space. Format the main partition as ext3 and mount it on /. Then continue with the install process :)

Instead of booting into OS X auto matically, your computer will boot into yaboot, which lets you select OS X or Linux.

I'm a little rusty, so I have got anything wrong please say.

---

### Post by ibookg4 on 2005-03-06
Thanks for your help.

Unfortunately, when I am unable to create consecutive partitions with Free Space.  Disk Utility keeps combining them, even if I select 'Locked for editing' for each partition that I created.  

I selected 'Volume Scheme' '4 Patitions' and set up the patitions as you said, and selected 'Partition.'

---

### Post by ibookg4 on 2005-03-06
The only way I was able to set up my partions as suggested was by formatting the Ubuntu partion as Unix is OS X's Disk Utility.  It appears that four partitions were created.  I was able to install OS X without any problems.

Next to Ubuntu setup. I got tot the screen for Partition disks and this is what I see:

IDE1 master (hda) - 30.0 GB TOSHIBA MK3021GAS
  #1  32.2    kB          Apple
         157.2  MB         FREE SPACE
  #3  8.9  MB             hfs+     external boo
  #4  10.7 GB            Apple_UFS_Un
         679.4 MB         FREE SPACE
  #7  18.4 GB           hfs+     Apple_HFS_un
         8.1 kB             FREE SPACE

When I select the second choice '157.2 MB    FREE SPACE' I get to a screen that ofers me three choices, no of them matching mentioning formating...
The choices are:

Create a new partition
Automatically partition the free space
Show Cylinder/Head/Sector information

I must admit I am somewhat lost.  Assuming that I partitioned correctly in OS X, what do I do next?  I would be a bit frustrated if I had to reinstall OS X again.

Thanks

---

### Post by godsunderstudy on 2005-03-06
[QUOTE=ibookg4]
Create a new partition
**Automatically partition the free space**
Show Cylinder/Head/Sector information
[/QUOTE]

Partitioning the free space will format it correctly.

---

### Post by ibookg4 on 2005-03-06
When I select '157.2 MB  FREE SPACE' and then 'Automatically partition the free space' I get this error message:

Failed to partition the selected disk
This probably happened because the selected disk or free space is too small to be automatically partioned.

---

### Post by Zarniwhoop on 2005-03-06
Really, all you need for the OSX part of the deal is a large chunk of free space in front of the OSX partition.  OSX is not wonderful at partitioning for linux, apparently it doesn't even understand the bootstrap partitions!  Not a problem, leave that for the ubuntu installer.

 What **will be** a good idea is to apply all available mac updates and security fixes after installing OSX and before you install ubuntu (the OSX kernel upgrades can overwrite the boot information, forcing you to boot from the CD in rescue mode).

 Summary - put a nice big chunk of free space in front of the OSX partition(s), install OSX, then use the ubuntu installer to partition the free space into the boot partition for yaboot (1MB), '/', swap, any other partitions you feel like.

---

### Post by r1kk1 on 2005-04-10
This is all I did for my g3 ibook:

Insert osx cd
Use partion manager found there.
My free space was on the back side of the hard drive.
Installed osx and did updates, etc.
Insert ubuntu cd holding c key.
when it got to the part of partion, I told it to use the free space and it did.

Both os's boot fine!

It was that easy.  The documentation says that free space should be in the first position of the hard drive but it didn't matter.

take care and enjoy,

eric

---

