---
title: "Partition Layout for clean install"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-10-26
I want to setup my partitions manually this time around to make future upgrades/installs easier. Here is the current situation: C: Vista (NTFS) 30 GB, D: Data (NTFS) 100+ GB, and Ubuntu Gutsy 80 GB. I plan to delete Vista and Ubuntu partitions using GParted from a LiveCD and then manually install. I need to leave the Data partition as it stores all my important documents and files. Can someone suggest a layout that would work? I am thinking expanding the data partition to take up the space from the ubuntu partition, and then shrinking it back down again so that the data partition is the last partition. Then installing Gutsy as follows:

/ 80GB
/Swap 4 GB (not sure what this number should be, I currently have 4GB of RAM but only 3.2 GB are                 
                    reported since I am using a 32 bit OS)
/Home 80 GB
Data (NTFS) 100+ (the rest of the space)

How does this sound? Any suggestions?

---

### Post by indytim on 2007-10-26
Partitioning is always a personal choice.  Having said that, I'd suggest assigning your "/" to 10-15G.  Make the "/home" larger to accomodate your doc's settings etc tied to Ubuntu.  Create a /swap =~ 2xRAM.  Should be good-to-go.  Adjust to your local environment.

IndyTim

---

### Post by jba6511 on 2007-10-26
thanks. Is it as simple as creating 3 partitions in GParted, the / as ext3, the swap as swap and the /home as ext3? Also, will 8GB of ram (2x my amount) really be necessary? Could I get away with a lower amount?

---

### Post by indytim on 2007-10-26
Yes, basically it is that simple.  After you ahve created your partitions, jsut note which partition is which is sda4=swap sda5=/ sda6=/home.

Re the swap, I guess I'd recommend using 2G for /swap.  Sound like your h/w is pretty complete and up-to-date with that much RAM.

Don't forget during the manual install, you will have to check the "/" as being formatted even though it is already formatted.  Also, one other thing.  if you want to give your data partition a more descriptive (keep it short) title rather than /sda17, while in the partition set up, click the Setup or Configure or whatever button for that partition.  Change the /media/sda17 to say /media/Data.

In the past 10 or so installs, I've always gone with pre-configured partitions with consistently no surprises.

Good Luck,

IndyTim

---

### Post by blu3ness on 2007-10-26
I recommend a layout where you have a NTFS partition for vista, a shared partition, FAT32 or ext2 of 120g or more for your data and files to be SHARED by vista and linux.

and a seperate 10 gb partition for /, and a few gigs for swap.

My friend did it that way and I like it very much.

Personally i hate syncing data between ubuntu and windows all the time, despite the NTFS-write support driver, it's still a pain because you have to cleanly exit windows.

---

### Post by Niniel on 2007-10-26
Regarding the swap partition, my admittedly limited experience suggests that you don't need a lot of space for that. 
On my 512 MB RAM laptop computer, I started out with 1GB since I had read that swap = 2 x RAM = good idea. However, after I installed the system monitor taskbar application with a swap monitor, I was shocked to realize that the swap file was always reported as being 100 % available. Sometimes I would get 5 % (edit: use, not free space left), but that was it. 
I then shrank the swap partition to 512 MB and the same is happening - according to the sys mon tool, my computer is almost never using swap space. I'm not quite sure how accurate the tool is though since I still get 5 % use readings sometimes. 

Maybe somebody with more experience can shed some light on this. Some applications may need a lot of swap space, but I don't know if applications even use the swap partition, or if they manage their own swap space (like Photoshop does).

---

### Post by Niniel on 2007-10-26
> **blu3ness said:**
> I recommend a layout where you have a NTFS partition for vista, a shared partition, FAT32 or ext2 of 120g or more for your data and files to be SHARED by vista and linux.


You can use an NTFS partition to share data. My Gutsy installation is more than happy to read from and write to my Windows partition, so really, I don't see any need to mess around with FAT32 anymore.

---

### Post by jba6511 on 2007-10-26
well I will not need vista anymore. I have not booted to it in months and when I do I will just use it in virtualbox. Thanks for the info guys. Now if some expert come shed some light on the swap I think I will be all set.

---

