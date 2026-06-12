---
title: "how to mount hard drives"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by md_jamil on 2007-03-04
I have winxp on my machine I am puppy linux user, in puppy its very easy to mount and browse windows partitions in fact all drives, I am lost in Ubunto how to mount hard disk partitions, I looked in help its tells you to go to pulldown menu administration and disks but in my case there is no disks option in any pulldown menu. what wrong ?

---

### Post by taurus on 2007-03-04
Here you go.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by chggr on 2007-03-04
First of all, you need to know which device corresponds to the partition you want to mount.
You can find this by using the Device manager:
1)System -> Administration -> Device Manager
2) Locate your hard disk drive
3) Pull down the menu of the drive and find something like "Volume (ntfs)". Click on it
4) Select the "Advanced" tab and find the value of the property "block.device". This value should be something like /dev/hdXY where X is a letter (a,b,...) and Y is a number (1,2,3)
This is the device you were looking for.

Next, make a folder in the /media folder using the command line ("Applications" -> "Accessories" -> "Terminal":
sudo mkdir /media/WindowsPartition

Finally use this command  to mount the partition onto that folder:
mount -t ntfs -o umask=000 /dev/hda1 /media/WindowsPartition

Where /dev/hda1 will be replaced with the device which corresponds to the partition.
Now you should be able to access the contents of your partition under the folder /media/WindowsPartition. If you want this process be done automatically for you every time you boot up, you have to edit the /etc/fstab file and add this line (replace /dev/hda1 with your device)

/dev/hda1       /media/WindowsPartition  ntfs    rw,user,auto,umask=000   0       0

---

