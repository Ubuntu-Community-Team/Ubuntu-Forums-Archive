---
title: "Installing Ubuntu, NEED HELP NOW"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Atari26003 on 2007-10-15
im on laptop an acer 5012WLMI
Anyways,
when it omesup as use whole disk or manual for partition 
Do i select manual or just let it do something on its own,
i have a pre partitioned drive, from acer,
i want a DUAL boot not overwritting windows,
o.o'
It says there is 3 to choose from ( i know one is the settings, and one of other is windows partition)
But when i try selecting third one it says no root?
im on the menu right now,
im worried about messing something up,
how doesn't it hav a root?

---

### Post by Duck2006 on 2007-10-15
This sould help

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Atari26003 on 2007-10-15
it does not give me 3 options
gives me two
Manual or use entire disk

---

### Post by MatthewPlanchard on 2007-10-15
To dual boot you'll have to use manual. Resize your old Windows partition and create a new Ext 2 filesystem in the unpartitioned space, as well as a smaller Swap partition. (I say Ext 2 and not Ext 3 because I heard many have problems getting the GRUB to install on Ext 3)

Use the manual settings to set up the Ext 2 partition as /

You should be good to go.

---

### Post by Atari26003 on 2007-10-15
here is my options
and a screenshot of error
[IMG]http://i77.photobucket.com/albums/j46/Atari26003/Selection.png[/IMG]
[IMG]http://i77.photobucket.com/albums/j46/Atari26003/Error.png[/IMG]

---

### Post by Atari26003 on 2007-10-15
> **MatthewPlanchard said:**
> To dual boot you'll have to use manual. Resize your old Windows partition and create a new Ext 2 filesystem in the unpartitioned space, as well as a smaller Swap partition. (I say Ext 2 and not Ext 3 because I heard many have problems getting the GRUB to install on Ext 3)

Use the manual settings to set up the Ext 2 partition as /

You should be good to go.

i sent screenshots
o.o'
under manual care to help me?
The first one is my laptops settigns
the second is my window
and the 3rd is acerdata ( where i want to save my files to)

I have backedup everything and i wana reformat that acerdata partition and put it there
How can i go about aking an EXT2  file system

---

### Post by wheredidrealitygo on 2007-10-15
okay, so after you select manual, on that screen where you have the three choices, here is what you have to do.

select the row that says "/dev/hda3 fat32 /media/hda3" and click "Delete Partition".

Then, it should say "free space", after that. select the "free space" row and click "new partition". it should ask you a few questions, don't touch any of them except which filesystem and which type.

change the mount point to "/" (without the quotes) and the type to "ext2" (or ext3, up to you).

"/" is your root system, it will be *like* your C: in windows.

Any other questions feel free to post again.

---

### Post by perce on 2007-10-15
> **wheredidrealitygo said:**
> 

change the mount point to "/" (without the quotes) and the type to "ext2" (or ext3, up to you).



I really suggest EXT3: it is much less likely to loose data in case of a sudden and unclean shutdown.

---

### Post by PmDematagoda on 2007-10-15
You need to have these partitions:-

Maximum of about 100Mb for a partition (ext3) with the mount point "/boot"

Recommended 2Gb for a partition (ext3) with the mount point "/"

A swap partition depending on your RAM, tell us the amount of RAM you have and we can suggest a good amount.

The remainder for your /home partition which will also be ext3(recommended)

---

### Post by k3lt01 on 2007-10-15
Acer tends to have a C:/ drive and a D:/ drive. D: is almost always the My Documents folder. I have a similar machine. If you have anything on the D:/ drive you want to keep MAKE SURE you copy it to the C:/ drive. You will have to do this in Windows. Just right click on the "My Documents" folder and move it to the C:/ >Documents and Settings> User> <Your user name> folder.

OK, Now you have saved what you want to keep, you can put Ubuntu onto  onto the Linux equivalent of the D:/ drive. This would probably be "hdb"

EDIT: Just had a closer look at your screen shots (sorry Hayfever season) and your ACER disk iand ACERDATA are your C:\ and D:\ drives (which one is which I cannot tell you but you could find out just by checking the disk "Properties". I don't understand why the partitioner doesn't recognise the separate drives as hda and hdb.

---

