---
title: "Ho much do I Partition"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-15
Hey Just about to install Ubuntu. I have a 120 GB hard drive. How much do I Partition?

AeThEr777

---

### Post by canadianwriterman on 2008-04-15
It depends on whether you already have another OS on the HD. 50GB would be plenty, depending on how much data (videos, etc.) that you might save into the home directory.

---

### Post by Medieval_Creations on 2008-04-15
Partitions can be very subjective...  So there really is no right way...

But my suggestion for a 120GB with just Ubuntu would be as follows.

20gb - /
30gb - /home
68gb - /mnt/Storage  #just space to put various things like music, pics, vids & what not.
2gb - swap

But you can set it up however you desire.  Aside from your root partition /, a swap of double the amount of ram in you rig is the only partitions you really need.

---

### Post by AeThEr777 on 2008-04-15
ok im at the prepare disk space screen just as im about to install. It has a few options. Guided - resize SCSI1 (0,0,0),partition #1 (sda) and use freed space
Guided - use entire disk
           -SCSI1 (0,0,0)(sda) - 120.0 GB ATA WDC WD1200BEVS-)
Guided - use the largest continuous free space
Manual

Pretty much I want windows completly gone and a few different partitions for music and documents. So how do i get that done. Sorry if this is really specific i just have no idea what to do. 

AeThEr777

---

### Post by Medieval_Creations on 2008-04-15
If you are looking to completely blow out windows... You can use the Guided - Use entire disk.  Ubuntu will setup the partitions for you (root & swap)...  If you want to set it up more like my previous example you would want to select Manual.  From there you can remove or add partitions and set their mount points as needed.

---

### Post by AeThEr777 on 2008-04-15
If I just let The intaller build up the partitions will they be divided at all like you had them or is it just a general partitioning?

---

### Post by AeThEr777 on 2008-04-15
How exactly do i know what to set up the mount points as? And type (fat32 etc.) Sorry I am very very very new to this and am completly linux stupid.I would much rather have a setup like you said where I have alloted disk space for music videos etc.

---

### Post by AeThEr777 on 2008-04-15
Anyone?

---

### Post by tvtech on 2008-04-15
general rule for size 

1gb for boot

4gb min for /    "this is root for windows users"

4gb min for /home

swap = at least 2X your ram if less than 1gb  at least 2X your ram if you want to suspend hibernate your computer specifically hibernate this is where your ram info gets cached for hibernation.  

my system if I were to do it would be 

/boot  = 1gb
swap = 2X ram
/root = 20gb  no home partition cause I do fresh installs

also note you can use [gparted]("http://gparted.sourceforge.net/") at any time in the future to change the size of your root partition if need be 
you can install it in ubuntu* username@localhost:~$sudo apt-get install gparted*

and then make another partition I'd say the rest of the size of your disk for media if you want to easily access it from windows make it ntfs or fat32 if you'd like to easily access it from a mac with osx versions earlier than leopard and windows

---

### Post by Medieval_Creations on 2008-04-15
If you use the Guided - Entire Disk, it will only create 2 partitions... Root & Swap.  Which in truth is all you really need.

Why don't we start here... what do you plan on using the PC for and do you have a specific reason why the standard setup from the guided partition won't work?

I'm currently at work and not on a linux box, so I can't get to detailed on the screens from memory, but if you go into the Manual partition setup it's pretty easy to get the hang of.

You can add or delete partitions from the main screen.  (the specifics I can't explain right now, because I'm working from memory).
Once you have the partitions divided up you can then edit the individual specifics of each.
The 3 you'll need to alter to your needs are;
The File System Type (ext3, fat32, etc...)
The Mount Point (/, /home, /var, etc...)
Format (Yes/No).

I've never really played with the rest of the options.

---

### Post by AeThEr777 on 2008-04-15
Thanx alot Helped out a ton! 

AeThEr777

---

