---
title: "Questions Regarding Partioning and MEMtest"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by xxneilxx on 2008-04-20
I downloaded the Beta version of HEron. 
I managed to do a checksum, and sucesfully burn it on to a cd.

[COLOR="Red"]I booted my PC
I chose my desired language
I did a error scan for my CD (no errors found)
I then did a mem test, it had 4 sucessful scans after which i got this:

Faill Address

0000f02bc00 - 240mb
0001002bde0 - 256mb

good
00002000
00002000

bad
00003000
00003000

The memtest continued running, after findiang ths,  cliked esc, and it said it was halting for 15min. I manually shut down and restarted.[/COLOR]

[COLOR="Blue"]I then chose my language and decided to run Ubuntu live, it took a while to boot. The OS is great, i enjoyed it. BUt i wasnt able to acess my internet, i have a cable broadwand hooked up to my ethrnet card. It works fine on xp. Is this beacuse i was running live.[/COLOR]


Finally i downloaded a copy of Ext2IFS_1_11. 
Have two harddrives the first one is for xp, and the second one is split in to two drives d and e. The firstone is an NTFS, the other two are FAT 32.

I plan on installing Ubuntu on D, firstly does the installation make sure that D change from a FAT 32 to and EXT 3. Secondly does the installation format the drive its being installed on. Drive d basically contains my previous XP os , but its not in use. DO i need to format it manually or does ubuntu take care of it for me. 

Please guide this lost soul

---

### Post by Hieronymus on 2008-04-20
When you start the installation of Ubuntu it will guide you trough to the partition manager. Chose the manual option and you can than pick onto which partition you want to install. 

Just delete the D drive, as you call it, and re-allocate the un-allocated space. You should make at least 2 drives: 

one format as swap (2 times the size of you internal memory)
one mounted as / and format it as etx3, at least 10 Gb. (or reiser, whatever you prefer).

When you then write the changes to you drive all data on D is gone.

Jeroen

---

### Post by Happy_Man on 2008-04-20
Also, don't worry too much about memtest. If you can run an OS on your computer, you're fine. 

Regarding your ethernet card...
what model card is it? I've never heard of any ethernet card not working before, chances are there is some other issue.

---

### Post by Vermind on 2008-04-20
Hello,
So Your memory has a bit of bad in it. It may hurt, but it doesn't seem there's a lot of bad.

1. For Ubuntu, if You don't want to do the partitioning stuff, there is always [wubi]("http://wubi-installer.org/"), an installer that installs Ubuntu on Your Windows D drive in its own file. This does not require any partitioning, and it does not change Your computer's default boot loader. This has two advantages: if You choose to remove Ubuntu, it's just uninstalling from the windows list of applications / deleting the Ubuntu file and boot loader entry. And Your boot loader will not go crazy if You delete Ubuntu.

2. If You think You want to get rid of the D and do the install on a real partition, then You can first delete the D partition in Windows, by right-clicking "My computer" and choosing Manage. Then go to the "Disk Management" part, and right-click on your D partition and delete the volume.

After this, You can just tell the Ubuntu installer to make the partitions as it wishes, using the available free space.

If You install using method 2, and later choose to remove Ubuntu, do not start it by destroying the partitions in Windows. If You do, Your computer will not boot until You use a Windows cd to fix the Windows XP boot loader. A better way to remove Ubuntu is to first fix the boot with the cd, or a recovery partition, and then remove the Linux partitions.

---

### Post by xxneilxx on 2008-04-20
Thank you both for your replies. 

I wont worry about memtest, i
IC Plus IP1000 Family Gigabit Ethernet Aapter is my ethernet model. BUt since my internet is working in Xp it should work in the other OS. Maybe it was loadig but really slowly. I will fully install the UBUNTU and see if my internet is working. 

[I][COLOR="Red"]Just delete the D drive, as you call it, and re-allocate the un-allocated space. You should make at least 2 drives: 

one format as swap (2 times the size of you internal memory)
one mounted as / and format it as etx3, at least 10 Gb. (or reiser, whatever you prefer).

When you then write the changes to you drive all data on D is gone.[/COLOR][/I]

Thanks for this info, my D drive s my primary partion alredy and it is 18GB big. It shares the rest of my HD with my edrive which is also 18GB. I use my E drive to store music , program files, E is a FAT 32 drive. 

Since i want to allocate the whole of D drive to the Ubuntu software, i would have to make it a ext3 , so what program doi install in C (NTFS,WINDOW XP) to read and write whats happening on D (ext 3), and does ext3 read and writeto NTFS and FAT32 automatically.

---

### Post by Happy_Man on 2008-04-20
Ubuntu can read and write to NTFS and FAT32 out of the box. 

There are ext3 drivers available for Windows at [http://fs-driver.org](http://fs-driver.org) .

---

### Post by Vermind on 2008-04-20
Hello,
For Windows and internal hard disks with ext3, I would recommend Ext2IFS.
For Windows and usb memory sticks with ext2, I would recommend Ext2 FSD.
Ubuntu, when installed, can read/write both NTFS and FAT32 without problems.

---

### Post by xxneilxx on 2008-04-20
thanks downloaded the drives, i just noticed that my d drive doesnt let me format it. I right clicked my d driveand selected format, FAT 32. It said it couldnt format due to utiliteis running in it. As far as i know all the programs within this drive are dead, wthe windows xp which was on this drive is also not being used. I recently had a crash and installed a new XP on C and made it my primary drive, D drive is now for storage, but still contains my previus windows and programs etc. Does the installation oof ubuntu  take care of this???

---

### Post by Vermind on 2008-04-20
Hello,
[a little bit on partitioning]("http://www.psychocats.net/ubuntu/partitioning").
The Ubuntu installer can resize windows partitions, or delete them, but You have to be careful not to remove Your C.
[A partitioning and install guide for windows and ubuntu dual boot]("http://www.psychocats.net/ubuntu/installing").

---

