---
title: "triple boot snow leopard, windows 7, &amp; ubuntu"
date: 2010-01-22
forum: Apple Hardware Users
---

### Post by JAM15 on 2010-01-22
i have only tried the following on a MacBook Pro (santa rosa generation)

1. i started with a clean install of OS X Snow Leopard on my hard disk drive (i had not yet partitioned my hard drive)

2. after installing snow leopard, install rEFIt (a boot loader) and make sure it is working by restarting your MBP and pressing the option button (the first time) etc...

3. inside OS X snow leopard go to the applications folder > utilities > boot camp assistant
using the assistant partition your hard drive according to the desired capacity you want available for your windows partition....and when you reach the insert disc to start installation.....do NOT proceed.....choose the "install later" option...
Note: it is important that you do not install windows 7 at this stage, or else you will have to re-install it after adding an extra partition for ubuntu since partitioning will destroy proper booting from the windows partition

4. pop in the OS X Snow Leopard install disc and boot from the disc.....once inside chose disk utility from the menu bar.....
in disk utility click on the hard drive disk name (not on any of the partition names)....the hard disk name that includes the 2 partitions created so far...
when selected, you can see a "partition" tab in the available tools on the right part of disk utility
click on the partition tab, and then click on the graphic of macintosh hd (the OS X partition whatever you've named it) and click on the little "+" button
this will allow you to add an extra partition that you can resize either using the graphic or by typing in the desired capacity....
this will create a new partition which we will format for now using Mac OS Extended (Journaled)....

Note: you will now have three partitions and YES the windows partition will be the last partition (disk0s4) according to your partition map thus allowing you to install windows 7 and allowing it to boot properly

4. after partitioning, it's time for installation....
pop in the windows 7 disc and boot from the disc.....after all files are loaded...install windows 7 on the partition created via boot camp in step # 3.....YES it will show up in the list of partitions with the name C something <boot camp> blablabla......you can even format it along the process before the windows installation actually begins......
do not forget after installing windows (first part through booting from the disc and then the MBP will automatically reboot after which you have to chose to boot to the windows partition to complete the installation) pop in the os x snow leopard disc in windows to install boot camp drivers and then download the boot camp drivers update from apple.com/downloads for windows 7 support and install them

5. with windows 7 installed, pop in the ubuntu (i used xubuntu 9.10 but have also tried this using ubuntu 7.10) disc and boot from the disc.....and start the installation....when you reach the step of choosing which parition to install on or size or something......choose manual and click next....wait for the partition tool to load....locate the partition created (using disk utility earlier) for ubuntu and click on it then click on 'edit partition'....set the mount point as "/" and chose "ext3" as the format....(the partition will be automatically formatted when you begin installation)....when clicking next, it will warn you of the swap partition but you can safely ignore that.....continue with the installation steps until you reach the last step.....BEFORE CLICKING ON INSTALL.....in the last step, click on the "advanced" button and MAKE SURE to install the boot loader to the partition allocated for ubuntu in our case it will probably be the third partition (i.e. instead of hd(0,0) or something like that just type "/dev/sda3")
then click next and finish installation......

by now when you boot your MBP, you should have 3 options available using rEFIt, and all of them bootable and fully functional

side note:
1. you can edit the refit.conf text file do change how your boot menu looks like
2. for ubuntu drivers check: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) & [https://help.ubuntu.com/community/MacBookPro_SantaRosa](https://help.ubuntu.com/community/MacBookPro_SantaRosa)

---

