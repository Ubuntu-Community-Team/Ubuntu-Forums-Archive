---
title: "Some Newbie Questions"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-01-21
Well here are some newbie questions that i am  being asked:

1] How can we safely un-install Ubuntu without removing windows:

My solution: make the windows boot partition as NTFS, this will force ubuntu to install bootloader on the /root partition. Is this a correct solution?

2] A normal home user should create which which partitions and of what size, whereas from a home user i mean a person who uses internet in browsing, chatting, downloading, does office works including open office, pdf files, some graphics, listen to music, burns cds, does some programing so does need build essential compilers plus a good ide like Anjuta or Eclipse, needs network, and installs some other softwares like his own browsers or etc...

My solution:
I think
/home
/root
and
Linux-swap would be enough with respectly 3GB, 5GB and 500MB space.

Then many of my friends and i myself who downloaded and burnt the iso of Edgy Eft has been facing a lot of System hangs, i.e. system stops responding or too many Crash bug eports, what do we do? i shifted back to Dapper, but the Gaim doesn't work properly as mentioned in the other thread....

---

### Post by tommcd on 2007-01-21
1) to uninstall ubuntu see this:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
2) I partition like this:
/root (10-15 GB, should be more than enough).
/swap 2x RAM (if you have more than 1GB RAM you can probably limit swap to 1GB).
/home (what ever is left, for your personal files).
EDIT: I make /root and /swap primary partitions for performance reasons. I make /home a logical partition so it can be easily subdivided later if necessary.

When you talk about system hangs or instability, do you mean windows or ubuntu? I have set up 3 machines to dual boot, and I never had ubuntu cause a problem with windows.

---

### Post by xpod on 2007-01-21
You could always use the disk management utility in Windows to delete the Ubuntu partition then if you`ve got a proper XP cd you can type "fixmbr" at the recovery console or if like me you dont have an XP cd  you can download a 98 bootdisk or similar with the fdisk utility and do "fdisk /mbr"

The installer will ask you near the end of the install process if you want to install grub to the mbr or not,I`ve always just accepted this though so aint sure what the options are otherwise?

Not sure about your hangs.
Graphics drivers mabey?
Hardware??

EDIT:Too slow:p

---

### Post by Canis familiaris on 2007-01-21
I partition like this:
/dev/hda1    Windows NTFS                3GB
/dev/hda2    FAT32                              2GB
/dev/hda3    FAT32                              1GB
/dev/hda4    Extended Partition           
/dev/hda5    Linux SWAP                  500MB
/dev/hda6    Linux Root                      21GB
/dev/hda7    Home Folder                  11GB
/dev/hda8    USR Drive                       9GB

---

### Post by tommcd on 2007-01-21
> **xpod said:**
> "

The installer will ask you near the end of the install process if you want to install grub to the mbr or not,I`ve always just accepted this though so aint sure what the options are otherwise?



EDIT:Too slow:p

I have wondered about this myself. I believe the options in a dual boot system are:
1) install grub to windows MBR
2) install grub to your /root partition (set it as bootable during partitioning). 
EDIT: here are the options:
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

---

### Post by shoaibi on 2007-01-21
> **tommcd said:**
> 1) to uninstall ubuntu see this:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
2) I partition like this:
/root (10-15 GB, should be more than enough).
/swap 2x RAM (if you have more than 1GB RAM you can probably limit swap to 1GB).
/home (what ever is left, for your personal files).
EDIT: I make /root and /swap primary partitions for performance reasons. I make /home a logical partition so it can be easily subdivided later if necessary.

When you talk about system hangs or instability, do you mean windows or ubuntu? I have set up 3 machines to dual boot, and I never had ubuntu cause a problem with windows.

Hmmm okies, well the Ubuntu stops responding... [Ubuntu 6.10]

---

### Post by shoaibi on 2007-01-21
> **xpod said:**
> You could always use the disk management utility in Windows to delete the Ubuntu partition then if you`ve got a proper XP cd you can type "fixmbr" at the recovery console or if like me you dont have an XP cd  you can download a 98 bootdisk or similar with the fdisk utility and do "fdisk /mbr"

The installer will ask you near the end of the install process if you want to install grub to the mbr or not,I`ve always just accepted this though so aint sure what the options are otherwise?

Not sure about your hangs.
Graphics drivers mabey?
Hardware??

EDIT:Too slow:p

no the Ubuntu 6.10 or Ubuntu 6.06 doesn't ask me to where install the BootLoader.

---

### Post by shoaibi on 2007-01-21
Here is my Problem:
Data in FAT32=90GB roughly
Harddisk is 120GB.
How much for windows, how much for /home and /root?

---

### Post by tommcd on 2007-01-21
Well, for windows it depends on what you want to do with it. On my current system windows is 40GB because I need it to be big enough for installing games. On another system I had winXP down to 10GB because I only used it as a safety net in case I screwed up ubuntu and need to get online to figure out how to fix my ubuntu partition.
In partitioning for windows, remember you need about 15% of the partition as free space for windows defragmenting to work properly, plus you need space for the swap file. So figure out how much space you need for all your windows programs (right click on the C drive in My Computer to see how full it is) then add at least 20% to that to be safe. If you need to make room then delete or uninstall unneeded stuff from windows.
For ubuntu, as I said:
/root = 10-15GB
/swap = 2X RAM
/home = what ever you need for your personal data.
Choose "manually edit partition table" from the ubuntu installer. It is not as hard as it sounds.

---

### Post by tommcd on 2007-01-21
> **shoaibi said:**
> no the Ubuntu 6.10 or Ubuntu 6.06 doesn't ask me to where install the BootLoader.

At the very end of installing ubuntu you will see this:
[http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu](http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu)
Just select the default "yes" to install grub to the MBR.

---

### Post by shoaibi on 2007-01-21
> **tommcd said:**
> Well, for windows it depends on what you want to do with it. On my current system windows is 40GB because I need it to be big enough for installing games. On another system I had winXP down to 10GB because I only used it as a safety net in case I screwed up ubuntu and need to get online to figure out how to fix my ubuntu partition.
In partitioning for windows, remember you need about 15% of the partition as free space for windows defragmenting to work properly, plus you need space for the swap file. So figure out how much space you need for all your windows programs (right click on the C drive in My Computer to see how full it is) then add at least 20% to that to be safe. If you need to make room then delete or uninstall unneeded stuff from windows.
For ubuntu, as I said:
/root = 10-15GB
/swap = 2X RAM
/home = what ever you need for your personal data.
Choose "manually edit partition table" from the ubuntu installer. It is not as hard as it sounds.

Is i select "Manually Edit Partition" it take hell lot of time to load the next screen, and after that when i have created the partitions and try to apply changes, it hangs up the system, hoswing that partitions are being created, i have even tried to give that time, last time when it stop responding after showng that its applying changes of the partitons it was 9am, and it stopped responding and till 5pm it was showing the same screen with no response and even the pogress bar was stuck..

---

### Post by shoaibi on 2007-01-21
Thus to avoid that i cleanup some free space, and check the option "Use largest free space" and it does all by itself even the selection of bootloader drive...

---

### Post by tommcd on 2007-01-21
Formatting the disk takes a while, but it should not take nearly that long. What are your system specs? In particular, how much RAM do you have? The Live CD installer needs at least 256MB RAM (I think). If your computer has modest specs you may do better with the alternate CD. I prefer the alternate CD anyway:
For edgy:
[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)
For dapper:
[http://www.ubuntu.com/products/GetUbuntu/download#lts](http://www.ubuntu.com/products/GetUbuntu/download#lts)
Choose your country, select other installation options (for the edgy mirrors), then select alternate install CD.
Did you check the CD for defects, or check the md5sums?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also, be sure to burn the iso at a very slow speed.
If you have trouble with "manually edit partition table" option, you can select "resize IDE1 master" (the first option from the partition section of this guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
This will automatically create a /root and /swap for you. /home and /root will then be one big partition. Nothing wrong with that, except your personal data will not be separate from the OS. This is how I first installed ubuntu because it was easiest for me.

---

### Post by shoaibi on 2007-01-21
Well i have:
P4 3.0HT
D915GAV MB
256MB AM [Now], 796 MB RAM [at that time when it hung]

And does the alternate cd support GUI installation?
no i didn't check the CD as it takes hell lot of time.
And yup i always burn it at 4x.

[EDIT]:
and can i upgrade [dapper->edgy] Ubuntu using CD, or Internet is Essential? 
Upgrade Process i.e. Dapper-> Edgy destryes the /home, so i think i do need a separate /home, do i?

---

### Post by tommcd on 2007-01-21
> **shoaibi said:**
> Thus to avoid that i cleanup some free space, and check the option "Use largest free space" and it does all by itself even the selection of bootloader drive...

You could do that, but the option to "resize IDE master" may be better for you beacause you can then choose how big to make windows, and ubuntu will automatically fill up the rest. For example, if you have a 80 GB hard drive, you could select 40GB for windows. Ubuntu will then create a 39GB /root partition (with your /home as part of it) and a 1GB /swap (if you had 512mb RAM, for example).
Either way, just get it installed and learn how to use it. The next time you install it it will be much easier.

---

### Post by shoaibi on 2007-01-21
and by the way tommcd i have been using Ubuntu, its just not the very first time, but this is the first time facing these kind of poblems,
I have used Kubuntu 6.06, Ubuntu 6.06 and Ubuntu 6.10.

---

### Post by shoaibi on 2007-01-21
and by the way resizing Master will effect my data placed on the disk? i.e. suppose if i have 
Assume i have 40Gb HD, then
Windows Boot Drive: 10GB [2 GB Free]
Data Disk 1: 15GB  [5GB Free]

and i chose the resize option, what will it do.

---

### Post by tommcd on 2007-01-21
> **shoaibi said:**
> Well i have:
P4 3.0HT
D915GAV MB
256MB AM [Now], 796 MB RAM [at that time when it hung]

And does the alternate cd support GUI installation?
no i didn't check the CD as it takes hell lot of time.
And yup i always burn it at 4x.

[EDIT]:
and can i upgrade [dapper->edgy] Ubuntu using CD, or Internet is Essential? 
Upgrade Process i.e. Dapper-> Edgy destryes the /home, so i think i do need a separate /home, do i?

That system should be fine for the live CD, but I would use the full 796 MB if you can put it back.
The alternate CD is all text based. Same thing, but without pictures. No need to worry, you don't need to know command line stuff to use it. Just use the arrow keys, the tab key, and the enter key. 
For the live CD it has the option to check the CD for defects when it boots up. It does not take very long.
If /home and /root are one big partition you may not loose your data if you upgrade from dapper to edgy. A clean install of edgy will destroy your /home however. To upgrade to edgy from dapper:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
I prefer clean installs to dist-upgrades, less likely to cause problems. But I think you are getting ahead of yourself. If you have a dapper disk, just install it and get it working, or download an edgy disk and install that.

---

### Post by shoaibi on 2007-01-21
i have both on Disc, i have tried both and tasted.
Butt Dapper is more stable on my system, unlike Edgy which stops responding after every minute...

[EDIT]
And by the way a clean install will mean installing the softwares that i installed before again?
I am person with Speed Limitation as well as Bandwidth Limitation.

---

### Post by tommcd on 2007-01-21
> **shoaibi said:**
> and by the way resizing Master will effect my data placed on the disk? i.e. suppose if i have 
Assume i have 40Gb HD, then
Windows Boot Drive: 10GB [2 GB Free]
Data Disk 1: 15GB  [5GB Free]

and i chose the resize option, what will it do.
Ok, I see what you are doing now. That is a good question. I have wondered about that myself. I suppose manually editing the disk would be best. I don't know why it would hang with your specs.
Sorry, but from the title of your thread I assumed you were installing ubuntu for the first time.

---

### Post by shoaibi on 2007-01-21
No need to say sory, it was my mistake, i started asking my question in this thread which should have been a separate thread, the first post of the topic were newbie questions and those were the questions asked by my friends.....

And about hanging up, well i have downloaded ISOs from 3 different locations, burn them at 4x, still they all hung my system up at the exact same screen.....
I wonder if some good person could send me pre-burned CDs.
Anyhow i am running Dapper Drake now a days, so many bug reports are geneeated every minute, that some times i have my head in my both hands....

---

### Post by tommcd on 2007-01-21
The ubuntu live CD has gparted on it (system>administration>gnome partition editor (Ithink that is what it says). Anyway, you could boot from the live CD, resize the disk with gparted to make some free space, and install ubuntu to the "largest free space" you create from the live CD with gparted.
I just remembered about gparted on the live CD.

---

### Post by shoaibi on 2007-01-21
> **tommcd said:**
> The ubuntu live CD has gparted on it (system>administration>gnome partition editor (Ithink that is what it says). Anyway, you could boot from the live CD, resize the disk with gparted to make some free space, and install ubuntu to the "largest free space" you create from the live CD with gparted.
I just remembered about gparted on the live CD.
Hmmmm same is the thing that i told earlier, that's what i do nomally....

---

### Post by shoaibi on 2007-01-22
Still my problem is unsolved: i.e.
can i upgrade [dapper->edgy] Ubuntu using CD, or Internet is Essential?
Upgrade Process i.e. Dapper-> Edgy destryes the /home, so i think i do need a separate /home, do i?
And by the way a clean install will mean re-installing the softwares that i installed before again?
I am person with Speed Limitation as well as Bandwidth Limitation.
Can i install KDE on Ubuntu from Kubuntu CD?

---

### Post by shoaibi on 2007-01-28
no help as of yet....

---

### Post by compwiz18 on 2007-01-28
> **shoaibi said:**
> Still my problem is unsolved: i.e.
can i upgrade [dapper->edgy] Ubuntu using CD, or Internet is Essential?
Upgrade Process i.e. Dapper-> Edgy destryes the /home, so i think i do need a separate /home, do i?
And by the way a clean install will mean re-installing the softwares that i installed before again?
I am person with Speed Limitation as well as Bandwidth Limitation.
Can i install KDE on Ubuntu from Kubuntu CD?

If you have an Edgy CD, stick it in, and run **sudo apt-cdrom add** and follow directions.  Next run **sudo apt-get update** and the do the upgrade.  Should use files off the CD.  Repeat the process with the Kubuntu CD to install KDE.

Upgrading should not destroy /home

---

### Post by shoaibi on 2007-01-29
Can i install KDE on Ubuntu 6.10 from Kubuntu 6.06 CD?
Both DEs has there own set of softwares, what of the softwares that i will install myself, will they appear only in the DE i isnatlled them? or in both?
And by the way how much extra space KDE will be needing and how much XFCE?

---

