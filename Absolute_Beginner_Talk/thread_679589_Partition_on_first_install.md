---
title: "Partition on first install"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by TimCor on 2008-01-27
Hi all

I would justlike to say thanks for the previous assistance and I have now installed Ubuntu on one of my PC (Still a few problems, but getting them sorted).

This problem. Laptop (Sony FE21S) 160 GB HD 2GB Ram running XP home. Installing   
HD partitioned C : 140GB (with windows) and D : 20GB with nothing. I want to install Ubuntu on D drive

When I boot from CD the install screen shows four options Guided with a slider, Guided use entire disk, Guided use largest continuous free space and Manual.

If I use the slider I get a new partition size, but I tried this to allocate 20% for a new partition but Ubuntu seemed to take the whole disk. Windows was still there but with little space left.

What option should I use to get Ubuntu in 20GB and XP in 140GB
If I re-partition the whole HD  where do I put the slider ?
If I don't re-partition what install option do I need to get Ubuntu on the 20GB partition

Please help, so that I can move forward with this OS.

All the best

Tim

---

### Post by LaRoza on 2008-01-27
My way of setting it up is to make the Windows partition and the Linux partition small, 15 GB in my case. I have a 512 Swap partition, and the rest of the drive is used for a fourth partition. This way, your data and files are not tied to the OS. 

This data partition is best formated as NTFS (format it from Windows)

You can set up the partitions with the GParted live cd then do a manual (no slider) partition and just select the partitions you created and make a mount point (in /media/) for the data partition. You can remap your My Documents folder (so the menu entries aren't dead) to this partitions as well.

The link to download the GParted live cd is in the link in my sig.

Windows needs an NTFS partition (what it calls C:), Linux should use an EXT3 partition (for /) and the swap file is swap. Create the partitions and install to them.

You can do the same thing for you setup, setup an ext3 partition in the unused space, create a swap partition, then select them in the Manual option.

---

### Post by bumanie on 2008-01-27
If I were you I would get a copy of gparted live cd (open source partitioning program)from [http://gparted.sourceforge.net/and](http://gparted.sourceforge.net/and) use it to alter your partition sizes to what you want. Before doing so it is a good idea to back up anything important and to defrag your windows machine. Gparted is very good at this function and I have never had it muck up the file systems.

---

### Post by TimCor on 2008-01-27
Hi 
I have created a GPARTED iso Cd but when it is run on my laptop, the graphics are unreadable. I can see that the mouse pointer is moving, but nothing else - Help again

Many thanks

tim

---

### Post by bumanie on 2008-01-27
> **TimCor said:**
> Hi 
I have created a GPARTED iso Cd but when it is run on my laptop, the graphics are unreadable. I can see that the mouse pointer is moving, but nothing else - Help again

Many thanks

tim

Have no idea why that is happening. Did you burn the cd at a slow speed? If not, it could be burning errors happening. Retry a burn at 4x burn speed and see how that goes. The slower the burn, the less errors one gets.

---

### Post by TimCor on 2008-01-27
Hi again

---

### Post by drowner on 2008-01-27
> **bumanie said:**
> Have no idea why that is happening. Did you burn the cd at a slow speed? If not, it could be burning errors happening. Retry a burn at 4x burn speed and see how that goes. The slower the burn, the less errors one gets.

I had serious graphical issues in the past using a gparted liveCD.

I use a little distro called 'RIP LInux' (recovery is possible) which has the same partitioning tools and a whole heap of handy recovery things when i want to do that sort of stuff.

Wiki it - theres a good run down, and a link to download it.

Its a little more complicated, but it works really well.

---

### Post by derred on 2008-01-27
Can't you just go into the manual partitioning and delete the 20gb partition after that you can restart the install and say to use the largest continuous free disk space(presumably the one you just made)?
Alternatively you can go into manual partitioning and do it all by yourself. My setup would be a 5 gb primary root (/) partition in ext3, a 11 gb primary home (/home) ext3 partition and a 4 gb secondary swap partition.
If you need more details just whistle :)

---

### Post by TimCor on 2008-01-27
Hi All

Many thanks for all the prompt help. I finally did it by using the partition slider in the "opposite" direction (miss reading the instructions as usual). Now in stalled and connected. My next problem is the printer using a print server !

I have a Canon printer (driver available in Ubuntu) which (in windows) prints to a 'Print server port (LK...)'. 

No printer is detected when Add New printer is selected and no 'ports' are shown.

My laptop has a wireless connection to a router then the router is wired to a print server which is then connected to the printer via a USB cable.  

This works fine in Windows as I can specify a "New port" for the printer, but Ubuntu does not give me that option, as far as I can see.

I am sorry to be a pain, but i am determined to get this brilliant OS up and running so tha I can show it off to other local PC users.

All the best

Tim

---

