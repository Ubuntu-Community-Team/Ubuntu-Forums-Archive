---
title: "Dual Boot with a twist"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by Baasha on 2006-05-15
I am a total noob with Ubuntu.  I want to install it as a dual boot system along with my present Win2k.  If everything goes as I expect it will, then eventually I hope to dump Windoze for good.  Hurrah!:D 

I have read as much as I can find on setting up a dual boot system, including the excellent step-by-step from 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

However, everything I have read so far assumes installing a dual boot system on the same hard drive.  I wish to keep Windows and Ubuntu completely separate on different hard drives.  I want to configure my new hard drive with a Linux partition and a fat32 partition so I can swap files into the Ubuntu applications and leave all my Windows stuff on the original drive.

Unless I missed something in the instructions I am at a loss as to how to tell Linux to install itself on the new drive and to leave the other one alone.  Can anyone help me out?  Warning!  Although I am reasonably comfortable with Windows, I am completely new to Linux, so please make it as simple as possible.

Thanks in advance,
Bob

---

### Post by catlett on 2006-05-15
It will give you the second drive as an option. When the partitioner starts up it will list the master drive and the slave drive seperately. Just choose to install to the slave.
If you do the automatic install it won't make a fat32 for data so your going to have to manually edit the partition table of the slave (second) drive to create the fat32 partition as well as the partitions for the linux install.

---

### Post by confused57 on 2006-05-15
[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

See if there's anything in these 2 links that may give you some ideas,  pay particular for instructions given by "lha".  It's how I have my system setup: Ubuntu master,  Windows slave;  easy to setup, works flawlessly, doesn't install anything to your windows drive.

---

### Post by nalmeth on 2006-05-15
The step's are almost identical.
Make sure that the new drive is set to slave (physically on the drive itself)
then use the ubuntu installer to install on device hdb (the slave) rather than hda (the master)
 
Just make sure you know which drive is master and which is slave, and pick hda/hdb accordingly

---

### Post by RAV TUX on 2006-05-15
[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

from aysiu

---

### Post by aysiu on 2006-05-15
It's actually *easier* to do what you want to do, since you won't have to resize your Windows partition.

Keep in mind that you don't need a separate FAT32 partition to share files. You can read/write Ext3 from Windows using [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by fornix on 2006-05-15
Yeah. Just make sure u select the correct drive while installing. hda stands for Ide0 master. hdb for Ide0 slave, hdc for Ide1 master, hdd for IDE1 slave. so depending on where u hav ur second hard drive installed, select the appropriate drive.  (eg: /dev/hdb1 for 1st partition on the hard disk /dev/hdb2 for 2nd partition and so on)

---

