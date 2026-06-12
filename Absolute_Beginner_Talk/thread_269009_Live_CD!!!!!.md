---
title: "Live CD!!!!!"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by laosboyme on 2006-10-01
I'am currently using live cd but i wanted to dual boot ubuntu with windows please help me...:confused: :confused: :confused: :confused:

---

### Post by devils_casper on 2006-10-01
HI !

LiveCD has an option for Install...
create an unpartitioned/free space... no formatting or labelling. only free space. you can use window's Disk Management Tool for this. 

Boot up through LiveCD and Click on 'Install' icon. during installation, select "unpartitioned/free space" for Ubuntu. dual boot is default. let installer do whatever it asks. you will get Dual Boot after installation.




casper

---

### Post by WalmartSniperLX on 2006-10-01
Ok first goto install. Follow the directions untill it asks you about the partition manager. What you want to click is:

-Manually setup partitions (or something like that)
-Then you want to right click your ntfs partition and click resize. 
-Remove as much mb/kb you need to make your linux partition
-Then when you finish that, you will make an unalocated data block
-Right click that and click create new (or something like that) and set the size of that and label the file system ext3
-Then make sure you left at least 1gb of unalocated space for a 'swap' partion (virtual memory)
-Use all the remaining space for 'linux-swap'
-Click next

(you might want to click next after each step just so it refreshes. Be careful, and make sure you dont have data fragments all over your ntfs partition when doing this. If you have ALOT of unused space then dont worry. If you get an error, defragment your ntfs partition in windows)

---

### Post by nthdegree on 2006-10-01
You need to first of all partition your hard disk, so you will want to use something like **gparted** to resize the Windows partition and create an ext3 formatted Linux partition.

You can then use the **Ubuntu Desktop CD** to install Ubuntu, during setup you simply format and install on to the Linux partition.  Either the setup will detect Windows for you *(not sure if that is implemented yet)* or you can alter the /boot/grub/menu.lst file after rebooting into your Ubuntu install.

Try to get as far as you can with setting up the multiboot following the advice I have just given and post about the problems you have, or if you need help with one specific problem.

---

### Post by WalmartSniperLX on 2006-10-01
> **devils_casper said:**
> HI !

LiveCD has an option for Install...
create an unpartitioned/free space... no formatting or labelling. only free space. you can use window's Disk Management Tool for this. 

Boot up through LiveCD and Click on 'Install' icon. during installation, select "unpartitioned/free space" for Ubuntu. dual boot is default. let installer do whatever it asks. you will get Dual Boot after installation.




casper

lol and THIS is the most simple way to get it done. Do this first :D lol but if you want to manually set it up you can use my way. I completely forgot about this option :D  ](*,)

---

### Post by nudnik on 2006-10-01
> **WalmartSniperLX said:**
> lol and THIS is the most simple way to get it done. Do this first :D lol but if you want to manually set it up you can use my way. I completely forgot about this option :D  ](*,)


Always remember... this ](*,) is the official mascot:mrgreen:

---

### Post by bigken on 2006-10-01
small tip defrag windows 1st ;)

---

