---
title: "New user...Patient..Willing..but stuck!"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by mordantae on 2007-12-20
Hi, 
first of all would like to say just how brilliant the ubuntu/linux community really is...
and say sorry in advance for my perhaps annoyingly verbose way of writing...hope i don't scare friendly helpful people away....

installed Ubuntu gutsy gibbon a few days ago, and have spent every subsequent day thereafter trying to get it all working. The forums have been a great help and I've solved many problems i had by just Googling and looking through the ubuntuforums and i didn't really want to post anything myself...guess i just don't like to bother anyone...

but i feel a little bit stuck at this point, since I'm (not alone but) completely new to Linux...

If anyone could spare the time to help...this is what I'm currently struggling with..

My Specs:
Processor:      AMD Athlon 64 X2 Dual core processor 3800+
Motherboard : Gigabyte GA-M59SLI-S4
RAM:               2GB 
Graphics:        NVIDIA 7950GX2
Hard drives     1 old IDE drive onto which ive installed Gutsy
                      and 2 SATA hard-drives..previously RAIDed...but now RAID disabled.

Firstly, on boot i'll get a hang on the

 kernel is alive
 kernel direct mapping tables blablabla 

which i fix by editing the grub stuff and taking away 'quiet splash ' and replacing it with 'noapic nolapic nosplash'  

this works fine, but i currently have to do this on every startup, is there anyway to find this information (text file somewhere) and edit it permanently? or fix it and have a nice splash screen wouldnt hurt my feelings :)

that's my small problem...

The real problems are with the Nvidia drivers and the SATA hard drives

As regards Nvidia drivers i dont think they're working correctly. I get some shearing and jaggedness i dont expect from my graphics card, ive also run the glxgears thing and it doesnt look too brilliant...

I tried downloading the installation file from the website and running it, but it wanted to be run as root...i couldnt seem to get round that problem despite forum combing...so i tried to reconfigure xserver-xorg ...which felt like a terribly bad idea as i was doing it as i  felt quite out of my depth... By this time i found out about Envy...installed it and used it...restarted, made sure the restricted drivers were enabled...

etc etc... i've noticed no considerable change in the graphics quality...should i be? maybe i just need some other way of testing whether or not its working...any help on this matter would be greatly appreciated.

(also while writing this ive had two crashes so far, mouse is stuck and i dont know what to do as regards keyboard shortcuts to get into anything that might save me from the crash plus i wouldnt know what to write if i got in there anyway)


my god this is getting stupidly long... :s  sorry


Last problem..

i cant get ubuntu to see my two 250GB SATA drives.
They were raided while i was running an xp environment prior to installing ubuntu, i have now disabled raid but i cant see them. Saw them in the live cd environment while i was installing ubuntu but never again after i had installed ubuntu.

i'm thinking maybe i need to update my bios but im unsure how to go about this as gigabyte offer an exe file...

tried navigating the cd gigabyte provided with the motherboard but i get into the folder with the Biod utilities and from then on im stuck. dont know what to click since exe wont work...

god you must be giving up by now...i'll post this now and hope someone out there is willing to read through this...

advise whether i'd get more help if i tried to post a friendlier shorter version of my woes...

Thank you SO much for your patience if you're actually reading this far down the post...

Regards.

---

### Post by dstew on 2007-12-20
> which i fix by editing the grub stuff and taking away 'quiet splash ' and replacing it with 'noapic nolapic nosplash'
To make these changes permanent, you need to edit the kernel line in the /boot/grub/menu.lst file.> i cant get ubuntu to see my two 250GB SATA drives.What do you mean by this? They don't appear on the desktop, or you cannot mount them? Do you see them in the output of the command **sudo fdisk -l**?

I'll let somebody else comment on the graphics problems.

---

### Post by psusi on 2007-12-20
You want to edit /boot/grub/menu.lst to modify the boot options permanently.  To use the two sata drives, you will need to format them and choose how to mount them.  What do you intend to use them for?  Just bulk data storage?  Do you want to keep them separate, or combine them in a raid0?  Post the output of sudo fdisk -l ( that's an L not a 1 ).

---

### Post by aonegodman on 2007-12-20
> **mordantae said:**
> 

Firstly, on boot i'll get a hang on the

 kernel is alive
 kernel direct mapping tables blablabla 

which i fix by editing the grub stuff and taking away 'quiet splash ' and replacing it with 'noapic nolapic nosplash'  

this works fine, but i currently have to do this on every startup, is there anyway to find this information (text file somewhere) and edit it permanently? or fix it and have a nice splash screen wouldnt hurt my feelings :)

that's my small problem...



Hi don't know if i can be of much help. Just learned how to edit and save the menu.lst file that grub uses to boot from by

sudo gedit /root/grub/menu.lst

Perhaps this is how you need to edit and save for your small problem.

---

### Post by mordantae on 2007-12-20
> **dstew said:**
> To make these changes permanent, you need to edit the kernel line in the /boot/grub/menu.lst file.What do you mean by this? They don't appear on the desktop, or you cannot mount them? Do you see them in the output of the command **sudo fdisk -l**?

I'll let somebody else comment on the graphics problems.


thanks a million *bows down in humble gratitude*

i managed to edit the menu.lst file ... so is this sort of like the equivalent of the boot.ini in windows ?? 

i ran 'sudo fdisk -l ' and yes i do see them..so i guess i have to find out how to mount them and do whatever else to them in terminal~? 

thank you very much for your swift swift reply :):)

---

### Post by mordantae on 2007-12-20
> **aonegodman said:**
> Hi don't know if i can be of much help. Just learned how to edit and save the menu.lst file that grub uses to boot from by

sudo gedit /root/grub/menu.lst

Perhaps this is how you need to edit and save for your small problem.

yeppetty that worked for me :) thanks for the reply!! but i used boot as opposed to root...

thanks!

---

### Post by mordantae on 2007-12-20
> **psusi said:**
> You want to edit /boot/grub/menu.lst to modify the boot options permanently.  To use the two sata drives, you will need to format them and choose how to mount them.  What do you intend to use them for?  Just bulk data storage?  Do you want to keep them separate, or combine them in a raid0?  Post the output of sudo fdisk -l ( that's an L not a 1 ).

well i was previously running windows xp with them raided in a striped 0 fashion...however i'm not sure i want to go back to this as problems with my much cursed xp installation meant i very damn well near lost all my data...and how much performance enhancement am i really getting out of it in the end?

i want to install a basic xp environment in a partitioned space on the sata, basically to run all my games,which i seem to have understood can't be done in linux? ... (please correct me if i'm wrong) and well...i dont want  xp for anything else apart from anything i might encounter brick walled in linux. 
ideally i purge windows out of my life but im ok with having it on there as a little game running harlot.

thankyou very much for your quick reply and being so helpful and informative :)

kudos

these are my results from sudo fdisk -l ....so they are being seen....

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd40dd40

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe89be89

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4795    38515806   83  Linux
/dev/hda2            4796        5005     1686825    5  Extended
/dev/hda5            4796        5005     1686793+  82  Linux swap / Solaris

---

### Post by dstew on 2007-12-20
It seems your two SATA drives are formatted in such a way that Ubuntu cannot identify the file system. If the SATA drive format was part of the previous RAID setup, you might be able to mount the disks as a RAID if you install the Linux **dmraid** program. See [this]("http://packages.ubuntu.com/dapper/admin/dmraid"). Maybe this is already contained in Gutsy, I don't know.
EDIT: You can install dmraid using Synaptic. Enable the Universe repository first.

---

### Post by tdeboeser on 2007-12-20
In reguards to your Vid... goto [Alberto']("http://albertomilone.com/nvidia_scripts1.html")s site.  I can't say enought about his script.  Envy will download, compile, and install the correct driver for you.

Oh, read the directions on his site.  the ubuntu version isn't the lastest.  

tom de

---

### Post by psusi on 2007-12-20
Yes, menu.lst is roughly equivalent to boot.ini in that it is a text file that the boot loader reads to figure out what boot options to present and what to load for each.  

The second disk doesn't contain a valid partition table because it used to be part of the raid0.  If you want to dual boot, I would suggest that you go back to using the sata drives as a raid0, and install windows there.  The performance gain is about double the speed, but also you don't have to manually mange what files go on what drive; you just get one big drive.  Install Ubuntu on the ide drive, and set up a fat32 partition on the raid to store bulk data that you can get to from both windows and Ubuntu.  You will need to install the dmraid package to get the raid working in Ubuntu.  For more information you might want to read the introduction of [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  Don't worry about all the instructions though, as they pertain to getting Ubuntu installed on and booting from the raid, you just want to access it to store data.

---

### Post by mordantae on 2007-12-20
> **dstew said:**
> It seems your two SATA drives are formatted in such a way that Ubuntu cannot identify the file system. If the SATA drive format was part of the previous RAID setup, you might be able to mount the disks as a RAID if you install the Linux **dmraid** program. See [this]("http://packages.ubuntu.com/dapper/admin/dmraid"). Maybe this is already contained in Gutsy, I don't know.
EDIT: You can install dmraid using Synaptic. Enable the Universe repository first.
hmm..how do i install it? can i do it through terminal? so i will need to make linux recognise the partition tables by installing dmraid (seeing as its not seeing it as containing any valid ones) before i could format them at all and then raid or not raid them?

my lord so many questions hehe...
but it beats looking at idiotic windows error codes and blue screens any day

having problems but STILL loving ubuntu...now thats got to be good..!

---

### Post by thelatinist on 2007-12-20
> **mordantae said:**
> these are my results from sudo fdisk -l ....so they are being seen....

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd40dd40

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Assuming you don't want to use these as a raid array, you can mount them using standard procedures.  First you will need to partition these disks and format them to ext3.  Use Gparted to create one primary partition on each disk and format it.  These partitions should become sda1 and sdb1.

Then do the following:

```

sudo mkdir /media/sda1
sudo mkdir /media/sdb1
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

```

Add the following lines at the bottom of the fstab file:

```
/dev/sda1 /media/sda1 ext3 defaults 0 1
/dev/sdb1 /media/sdb1 ext3 defaults 0 1

```

The first two commands create mountpoints for these disks.  The third backs-up your fstab.  The fourth opens fstab for editing.

The two lines added to fstab mount your two sata disks at /media/sda1 and /media/sdb1 using default options.

You can always create mount points using different names if you like, just be sure to change the folder name in fstab, too.

---

### Post by mordantae on 2007-12-20
> **psusi said:**
> Yes, menu.lst is roughly equivalent to boot.ini in that it is a text file that the boot loader reads to figure out what boot options to present and what to load for each.  

The second disk doesn't contain a valid partition table because it used to be part of the raid0.  If you want to dual boot, I would suggest that you go back to using the sata drives as a raid0, and install windows there.  The performance gain is about double the speed, but also you don't have to manually mange what files go on what drive; you just get one big drive.  Install Ubuntu on the ide drive, and set up a fat32 partition on the raid to store bulk data that you can get to from both windows and Ubuntu.  You will need to install the dmraid package to get the raid working in Ubuntu.  For more information you might want to read the introduction of [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  Don't worry about all the instructions though, as they pertain to getting Ubuntu installed on and booting from the raid, you just want to access it to store data.

cheers!  off i go... :) i'll let you know if i manage or not...

wow...*blown away by forum helpfulness*

*walks off with a strange bemused beaming smile*

thank you to everyone

---

### Post by aonegodman on 2007-12-20
> **mordantae said:**
> yeppetty that worked for me :) thanks for the reply!! but i used boot as opposed to root...

thanks!

Ooops! glad you caught it. :oops:

---

### Post by mordantae on 2007-12-20
haha tis ok :) no need to blush just shows im learning! hooray for learning haha

---

### Post by psusi on 2007-12-20
> **thelatinist said:**
> Assuming you don't want to use these as a raid array, you can mount them using standard procedures.  First you will need to partition these disks and format them to ext3.  Use Gparted to create one primary partition on each disk and format it.  These partitions should become sda1 and sdb1.

Then do the following:


The disks will need partitioned first as their partition tables are invalid.  If you want to do that, you can boot from the livecd or install and fire up gparted for a nice gui method and pick the option from the menu to create a volume label after selecting the correct disk drive.  Choose a DOS/MBR type, then create a partition and gparted will format it to the type you choose.  If you want it purely for Linux, go with ext3, if you want to share with windows, go with fat32.  Alternatively you can use fdisk in the terminal to repartition the disk.  Type sudo fdisk /dev/sda and choose the delete menu option to delete any existing partitions, then create a new primary partition, then exit.  You should then be able to mkfs.ext3 /dev/sda1 to format the partition with ext3.

Since you want to keep windows around though, I suggest you go back into the bios and enable the raid again, and install windows to the raid.  

To install dmraid, you can either use synaptic in the gui, or from the terminal, type:

sudo apt-get install dmraid

---

### Post by mordantae on 2007-12-20
> **psusi said:**
> The disks will need partitioned first as their partition tables are invalid.  If you want to do that, you can boot from the livecd or install and fire up gparted for a nice gui method and pick the option from the menu to create a volume label after selecting the correct disk drive.  Choose a DOS/MBR type, then create a partition and gparted will format it to the type you choose.  If you want it purely for Linux, go with ext3, if you want to share with windows, go with fat32.  Alternatively you can use fdisk in the terminal to repartition the disk.  Type sudo fdisk /dev/sda and choose the delete menu option to delete any existing partitions, then create a new primary partition, then exit.  You should then be able to mkfs.ext3 /dev/sda1 to format the partition with ext3.

Since you want to keep windows around though, I suggest you go back into the bios and enable the raid again, and install windows to the raid.  

To install dmraid, you can either use synaptic in the gui, or from the terminal, type:

sudo apt-get install dmraid

thanks ever so much...im having a read of that wiki FakeRaidHowto...its almost good to have all these problems since learning about linux takes a super boost...ive been at this computer reading about all sorts and everything all day...:) haha i shan't rest till i do this! :) thanks so much for your help...i'll post back with hurrahs :wink: thanks again

---

### Post by mordantae on 2007-12-20
> **psusi said:**
> The disks will need partitioned first as their partition tables are invalid.  If you want to do that, you can boot from the livecd or install and fire up gparted for a nice gui method and pick the option from the menu to create a volume label after selecting the correct disk drive.  Choose a DOS/MBR type, then create a partition and gparted will format it to the type you choose. ** If you want it purely for Linux, go with ext3, if you want to share with windows, go with fat32.**  Alternatively you can use fdisk in the terminal to repartition the disk.  Type sudo fdisk /dev/sda and choose the delete menu option to delete any existing partitions, then create a new primary partition, then exit.  You should then be able to mkfs.ext3 /dev/sda1 to format the partition with ext3.

Since you want to keep windows around though, I suggest you go back into the bios and enable the raid again, and install windows to the raid.  

To install dmraid, you can either use synaptic in the gui, or from the terminal, type:

sudo apt-get install dmraid

wait a minute...so do i create partition for windows installation residence first and then format it to ntfs? then create further partitions in fat32 for bulk storage accessible to both linux and windows... yeah?

---

### Post by thelatinist on 2007-12-20
> **mordantae said:**
> wait a minute...so do i create partition for windows installation residence first and then format it to ntfs? then create further partitions in fat32 for bulk storage accessible to both linux and windows... yeah?

Don't use fat32 for anything.  It is an outdated, non-journalling filesystem.  You can use NTFS in Ubuntu by installing the ntfs-3g drivers or ext3 in Windows using any of several ext3 drivers.  I recommend using NTFS if you want a data share.  But I repeat, don't use fat32.

---

### Post by dstew on 2007-12-20
Your disks might be accessible without formatting. Dmraid might recognize the RAID setup as-is, if you haven't changed it. It understands several standard RAID formats, such as VIA software raid and nvraid.

Of course, you can always re-format the drives as other posters have suggested -- but then it won't be a RAID anymore.

---

### Post by psusi on 2007-12-20
> **mordantae said:**
> wait a minute...so do i create partition for windows installation residence first and then format it to ntfs? then create further partitions in fat32 for bulk storage accessible to both linux and windows... yeah?

If you want to install windows to the raid, then just make sure the bios sees the raid again, and install windows normally there like you did before.  If you want you can just leave some of the disk unpartitioned when you are installing windows, and create a shared fat32 partition once windows is up and running.

> **thelatinist said:**
> Don't use fat32 for anything.  It is an outdated, non-journalling filesystem.  You can use NTFS in Ubuntu by installing the ntfs-3g drivers or ext3 in Windows using any of several ext3 drivers.  I recommend using NTFS if you want a data share.  But I repeat, don't use fat32.

It may be old, but at least it is well understood.  Microsoft has never documented NTFS, so people have to make educated guesses about how it works.  ntfs-3g works well for many people, but I prefer to trust my data to facts instead of guesses.  Also the ntfs-3g driver does NOT use the NTFS journal, and the windows ext3 driver does NOT use the ext3 journal.

By the way, ext is just as old as FAT is.  ext2 was in wide use back in the 90s, well before fat was extended to fat32.

---

### Post by mordantae on 2007-12-21
hi, im sending you this in follow up of the helpful advice you gave me yesterday but i think something to do with being at the computer all day trying to make heads or tails of it all got to me and i didnt manage to get anywhere..having slept on it maybe i can get this going today...

now i can see half of my raided partition in  gparted

it comes up as /dev/mapper/jmicron_LEVIATHAN (LEVIATHAN being my old computer name) 

but getting into gparted from terminal gives me 

unable to open /devmapper/jmicron_LEVIATHAN -unrecognised disk label.

unable to open dev/sdb - unrecognised disk label.

I want to set up the partitions in gparted before i go to install windows on the raid. but first i need to get it to recognise the second sata in the raid array...sdb...how could i go about doing this?



-----------------------------------------------------

this is turning out to be far too much hassle..im going with the original plan and not bothering with raid...maybe in another life...now how would i go about removing the /dev/mapper/jmicron_LEVIATHAN entry from gparted? ive deleted the array and disabled raid from the bios. is there some strange reason why gparted still wants to look at half my previous raid?   thank you all for your time and consideration :) this is a beautiful community where i certainly can't say i feel alone or without places to turn for help...seriously...kudos to the entire community

---

### Post by Malta paul on 2007-12-21
Hi 
I think you will find the answer to you RAID setup, using  the Alternate disk- manual partitioning.
Hope this helps :guitar:

---

### Post by dstew on 2007-12-21
Using gparted, you should be able to **delete** the partitions that were once part of the RAID, even if your Ubuntu system cannot read them. After that you will have unallocated space. You can create new partitions out of the unallocated space.

---

### Post by Davidbmck on 2007-12-21
Hi all!

Looks like I'm in a very similar boat to the previous poster... I've just moved from Windows XP to Ubuntu gutsy. I previously had a drive setup in windows somewhat like:

Windows installed on one drive  (C: )

Two 120gb drives in RAID0 (S: ) as storage

Now, the linux filesystem is confusing the crap out of me, but I'm battling away with tutorials and whatnot to get my head around it. I just want to recreate pretty much what I had.  I've installed ubuntu onto the first drive, and let it format/partition it the way it wanted. I've killed the Windows RAID0 setup using gparted and created an ext3 primary partition on the two 120Gb, so I could just mount them and use them as seperate drives if I wanted I suppose.

The tutorial on fakeRAID in this forum is great but I don't trust my fakeRAID controller - it's caused me some grief in the past, so software RAID is what I want!

I am beginning to understand that I need to use mdadm to then turn those partitions into RAID... but I get unglued here!

---

### Post by Malta paul on 2007-12-22
Hi, Davidbmck
You need to install Ubuntu with the Alternate CD. which you can down-load.
Check out [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
And down-load Video 'Install_Ubuntu_2'  No 20070910 for info.
The part that will tell you how to set up Raid is in Manual partition section.
Hope this helps:)

---

