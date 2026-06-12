---
title: "Very big problem on Installation"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by L1nux01D on 2007-06-01
Have a problem on process during installation.When is time to choose partition it's show me:

1.Where is there 3rd option,where I can choose to erase XX % of all data?

[[IMG]http://aycu25.webshots.com/image/14864/2005650772522319886_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2005650772522319886)

2.Why my HDD is empty?I have 4 parts:

~15 GB Windows (C)
~55 GB Media (D)
~5 GB (EX root) I formated this tome into ntfs,but it was a root tome.
~512 MB (EX SWAP).

[[IMG]http://aycu25.webshots.com/image/14864/2005630983399910446_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2005630983399910446)

3.I don't want to fotmat my HDD ...Is there another option to install Linux?	[-o<

[[IMG]http://aycu04.webshots.com/image/19323/2005659080506688310_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2005659080506688310)

WERY BIG PLEASE:HELP ME!!!

---

### Post by Sparkster185 on 2007-06-01
What you need to do is pick the "Manual configuration" option on that first screen you posted.

Then you need to re-size your NTFS partition, which will free some space.  Now you have to create the partitions you want (/, swap, /home) and format them.

---

### Post by L1nux01D on 2007-06-01
Yes,I know.But when I press to create a new partition it shows me picture #3,,,,,,Wait a little and your Browser must load my uploaded pictures.

---

### Post by Sparkster185 on 2007-06-01
What you need to do is right-click that partition.  One of the options should be "edit", or something similar.  Use this to re-size that NTFS partition and free up space.  From there you can create new ones.

---

### Post by L1nux01D on 2007-06-01
This is the problem,that I Can't create a new partition,and resize.The installator says that my HDD is empty,when I click on a "Create a new partition" pops up a window which says:

A disklabel is a piece of data stored at a well known place on
the disk,that indicates where each partition begins and how
many sectors it occupies.
You need a disklabel if you want to create partitions on this disk.

By default GParted creates an msdos disklabel.

*WARNING: Creating a new disklabel will erase all data on /dev/hda!*

-------------------------------------

What should I do?

---

### Post by krisfrajer on 2007-06-01
What ubuntu are you installing?

If you are installing ubuntu from a cd live (you can download it from ubuntu web page, about 600MB) then you start ubuntu from the CD. What this will do? SImple, it will load ubuntu on your system without installing it in your hard drive. It will run slower since it is running from the cd but then you will have access to most of the ubuntu functions. You can use the disk management tool to resize your NTFS. Make sure you defrag your hard drive and back up your data. Resizing your hard drive has a small risk of lossing part/all the data. As far as today, in my experience, I have not heard any case of data lost when resizing, but still the risk is there. 

Then after the resize is done, install ubuntu from the live CD but clicking on the icon in the Desktop. One thing that you could do before that is to run a terminal window (applications>>accessories>terminal) and execute the comand 
fdisk -l
I think you have to execute this command as root: If so, then type "sudo fdisk -l"   and then it will ask you for the root password. The output of this command willl display the actual partition(s) of your HD. 

I hope this helps...

---

### Post by the_tavi on 2007-06-01
Hi,

I am also a new user, I just installed  Feisty Fawn 7.04 one week ago. So not much of a help from me...
If you didn't already deleted the entire disk (and I hope you didn't), you could also create a small boot partition (200MB in my case), in order not to overwrite the MBR.
See this:
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)
related to installation of a dual boot system.

Good luck!

Tavi

---

### Post by krisfrajer on 2007-06-01
you can also resize your HD from windows.... from the disk management utility.

---

### Post by Lucifiel on 2007-06-01
Hmmm.. maybe you can try using Parted Magic to create ext3 and linux-swap partitions.

[http://partedmagic.com/](http://partedmagic.com/)

I would not use Windows to resize your hard disk for the issue being that it sometimes do odd things to your partitions. Better to use a partition-dedicated utility.

---

### Post by L1nux01D on 2007-06-01
2 krisfrajer I'm installing Ubuntu 6.06 Dapper Drake.I had this OS on my PC before,and I'm NOT a complete newbie =).I formated 2 partitions from the "Disks Manager",formatted 2 parts into Memory Swap and Extented 3.Then i wrote in terminal and it shows:

omitting empty partition (5)

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1922    15438433+   7  HPFS/NTFS
/dev/hda2            1923        9729    62709727+   5  Extended
/dev/hda3            2679        9729    56637126    7  HPFS/NTFS
/dev/hda5            1923        2611     5534329+   7  HPFS/NTFS
/dev/hda6            2612        2678      538146    7  HPFS/NTFS

When I start again the installer,he show me the same picture,that my HDD is empty...

Here is the screenshot from the Disk Manager

[[IMG]http://aycu22.webshots.com/image/18701/2004961958598852322_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004961958598852322)

---

### Post by L1nux01D on 2007-06-01
Maybe I wrote something wrong....I DON'T NEED TO CREATE PARTITIONS.I NEED TO MAKE LIVECD SEE MY PARTITIONS ON HDD.LIVECD SAYS THAT IS EMPTY!!!!

---

### Post by krisfrajer on 2007-06-01
I am not sure what is the problem there... maybe try to format your partition as ext3 or if I were in your shoes... I will just erase the partition information where I want to install linux and then when you run the installers, the installer should display that erased partition as "unlocated space". That is what I would try at this point, other than that... I do not think I can offer you more help since that technical problem would be out of my league. Anyways, good luck!

---

### Post by Lucifiel on 2007-06-01
Quit using capital letters, please. Everyone here is helping you out on a volunteery basis. We don't help new users so we can get yelled at and humiliated. 

Anyways, the reason why we are trying to get you to create partitions is because it seems as though the Installer can't seem to detect either the empty partition or the empty space. It seems as though one of the partitions might be causing problems for the Installer.  

Go give Parted Magic a try before you insist that things don't work. Actually, do note that using Linux will require accepting various "solutions" and "walkarounds" with an open mind. 

And please behave like a matured individual. I don't care how old you are or who you are but please act with more grace. :p

---

### Post by the_tavi on 2007-06-02
I had some problems like yours, when trying to install. Finally I solved the issue using another tool : a bootable disk with Acronis Disk Director. I deleted all the empty partitions I had, keeping just the one with Windows, and formatted the new partition on the empty space created ( ext3, Normal, not Quick), After that, I was able to use the partitioning tool from the Linux bootable disk, recognizing without a problem the ext3 partition and also dividing it into needed partitions for Linux. It was perfect...

Good luck,

Tavi

---

