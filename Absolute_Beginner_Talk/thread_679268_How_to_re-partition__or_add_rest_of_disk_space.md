---
title: "How to re-partition  or add rest of disk space ?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by an4560 on 2008-01-26
Hi  there.. I just installed ubuntu7.1 and I did the manual partition with the following settings 

Have a 120 GB Drive 

Installed with following settings 

 / = 4GB
 /Swap = 1 GB
 /Home = 8GB 

How do add the rest of the space, so I can use it and where should it get added to  ? 

Thanks:confused::confused:

---

### Post by drowner on 2008-01-26
A few questions:

What would you like to do with that space?

Is this 120gig drive for Ubuntu ONLY - or are you sharing it with windows? Is there anything else on there apart from the 13 gigs above?

---

### Post by an4560 on 2008-01-26
I would like to store some of my music and pictures .. its ONLY Ubuntu 

I would not mind sharing that space out to other Windows Desktop that I have on my home network 

Thanks

---

### Post by amaroKer on 2008-01-26
If you don't have Windows on your computer, expand (resize) your /home partition to occupy the rest of the drive.

Hopefully, the /home partition is the last partition on the drive.  

Open System>Administration>Partition Editor

|-- / --|-- swap --|-- /home --|
Should have no problems resizing /home to desired size.

|-- / --|-- /home --|-- swap --|
Will require you to turn swap off (in partition editor, just right click on the swap partition and hit 'swapoff'), move it to end of drive, and resize /home accordingly.

Be careful not to format over or remove any partitions.
Hope this helps.

---

### Post by drowner on 2008-01-26
> **amaroKer said:**
> If you don't have Windows on your computer, expand (resize) your /home partition to occupy the rest of the drive.

Hopefully, the /home partition is the last partition on the drive.  

Open System>Administration>Partition Editor

|-- / --|-- swap --|-- /home --|
Should have no problems resizing /home to desired size.

|-- / --|-- /home --|-- swap --|
Will require you to turn swap off (in partition editor, just right click on the swap partition and hit 'swapoff'), move it to end of drive, and resize /home accordingly.

Be careful not to format over or remove any partitions.
Hope this helps.

Depending on the order of the partitions, this may or may not be possible. In that, he will not be able to unmount "/" if it is needed to be moved around/resized and if there are configuration files currently in use in /home then that shouldn't be unmounted either.

The ideal way to repartition would be to use a LiveCD (the ubuntu liveCD, or the gparted one, for instance). Then all the partitions can be unmounted.

Also, I have no experience with file sharing with windows disks. Perhaps someone who does could clarify if Windows can read a shared ext3 drive?

if it can, then make your /home bigger

If it cant, then add a shared partition - may need some fiddling around.

---

### Post by schiznik on 2008-01-26
> **drowner said:**
> Also, I have no experience with file sharing with windows disks. Perhaps someone who does could clarify if Windows can read a shared ext3 drive?Once it is shared, it can be read by anything with a samba/cifs client. This is of course assuming that you didnt mean shared for a dual boot system, which the OP doesnt have.

Even then, there are programs such as explore2fs, and some drivers that will let you mount ext3 as a windows drive letter.

> **an4560 said:**
> I would like to store some of my music and pictures .. its ONLY Ubuntu 
I would not mind sharing that space out to other Windows Desktop that I have on my home network 
Do as previous posts suggest, use the live CD to increase the /home partition to fill the rest of the disk, and share it from linux to windows with samba.

---

### Post by an4560 on 2008-01-26
Thank you all ,,,, Partition Editor worked great . :)

I created it as another partition /dev/sda4 - Fat32 .. so I hoping this will be visible from other Windows PC once I share it ... more testing to do ...  but its a good start .

Thanks Guys

---

### Post by schiznik on 2008-01-27
If windows and linux are on different PC's, its best to format it as ext3 (or another linux filesystem.)

FAT32 doesnt support permissions, and files larger than 4G. You only need this if you are dual booting on the same PC.

---

### Post by stephens on 2008-02-06
> **schiznik said:**
> If windows and linux are on different PC's, its best to format it as ext3 (or another linux filesystem.)

FAT32 doesnt support permissions, and files larger than 4G. You only need this if you are dual booting on the same PC.

i use to have a similar issue, that my extra parition fat32 of 40gb was not see on COMPUTER.

What i do is to download and install the GPARTED, and then an option of Partiton Editor appear, and i reformat the partition that was causing the problem with the program.

---

