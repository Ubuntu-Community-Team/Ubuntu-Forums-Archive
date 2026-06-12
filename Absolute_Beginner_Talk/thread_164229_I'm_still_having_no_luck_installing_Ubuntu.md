---
title: "I'm still having no luck installing Ubuntu"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by babel on 2006-04-22
I have made multiple attempts to use the Ubuntu Install CD version 5.10. 
I keep getting stuck at the same place.  

I am using a PC with 256 MB RAM & 20 GB hard drive running Windows 98 SE.  I am attempting to create a dual boot of Ubuntu & Windows 98.  Only 3.8 GB of the hard drive is presently used.

In the "Partition Disks" section, after I select "Resize IDE1 master, partition #1 (hda1) and use freed space" I arrive at the next screen.  This screen asks for the new size of my existing Windows partition I wish to choose.  I usually select the default, which is 12.1 GB.  Every time I try this I am told that the partitioner cannot perform this task.

I tried the manual partition but can't even find a way to select a new partition size in that.

I'm really stuck at step one of using Ubuntu and can't seem to move past it.  Does anyone have any suggestions?

](*,)

---

### Post by mips on 2006-04-22
Use gparted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Might prove easier to use.

---

### Post by Aessu on 2006-04-22
The partiotiner cannot resize your windows (fat32) partition for some reason. You can try to do this with another program in windows like the the partiotion magic. You can download a trial version of partition magic here: [http://www.soft32.com/Download/free-trial/Partition_Magic/4-151-1.html](http://www.soft32.com/Download/free-trial/Partition_Magic/4-151-1.html)

---

### Post by Mustard on 2006-04-22
I'd go with the above advice, from mips, and download the gparted live CD.  At least you get a graphical interface for partitioning that will allow you to 'see' whats going on.

---

### Post by skinnygmg on 2006-04-22
4G and 12G is 16G.  a 20G HDD is probably only 18G of real space.  ubuntu needs about 2G to install.  you may be giving windows too much space/not be giving ubuntu enough.  try typing "50%" when it asks you how much space, and ubuntu will split the free space between 98/ubuntu

---

### Post by babel on 2006-04-22
I will try Skinnygmg's "50% solution".

If that doesn't work I will download the gparted partitioner, although given my limited computer skills I'll probably encounter a few problems trying to use it!

Thanks for the replies, everyone!

---

### Post by babel on 2006-04-22
Well, typing "50%" didn't work either.  I got the same error message.  
I'll try downloading the "gparted" program.

---

### Post by babel on 2006-04-22
Next questions**:**

(1)  I downloaded this file:**** gparted-0.2.4.tar

But how do I open a "tar" file?

(2) If I use a program like "gparted" to create a partition, how will the Ubuntu Install CD know to install in that partition?

---

### Post by skinnygmg on 2006-04-22
[QUOTE=babel]Next questions**:**

(1)  I downloaded this file:**** gparted-0.2.4.tar

But how do I open a "tar" file?

(2) If I use a program like "gparted" to create a partition, how will the Ubuntu Install CD know to install in that partition?[/QUOTE]

you need a partition tool that runs in windows as you don't have linux up and running yet ;)
try Aessu's advice about the trial of partition magic

---

### Post by Buffalo Soldier on 2006-04-22
Sometimes a FAT/NTFS partition can not be resized because of fragmentation. Usually parted/gparted is not able to resize if there are files at the end of the partition. I would suggest booting into windows and defragment the partition 2 or 3 times. Then try to resize the partitions again. *Usually* that works :)

---

### Post by Mustard on 2006-04-22
[QUOTE=babel]Next questions**:**

(1)  I downloaded this file:**** gparted-0.2.4.tar

But how do I open a "tar" file?

(2) If I use a program like "gparted" to create a partition, how will the Ubuntu Install CD know to install in that partition?[/QUOTE]

I'm pretty sure you downloaded the wrong file to create a live CD. You would have gotten an .iso file of some kind if you were downloading the live CD.  I was just looking at the website myself and the links to the live Cd don't seem to be working anyway. :)

The advice to defragment the drive earlier seems like a good angle to try.

There are other options for live CD's to download that have graphical partition tools.  That one was handy because its a small download.  The fact that the links are not working is pretty disappointing though.

---

### Post by babel on 2006-04-22
skinnygmg**:**  Good point about the partitioner.  I certainly would need one that works in Windows.  

Aessu**:**  I will go with your advice & download the trial of Partition Magic next time I can sit down with the computer for a while.

Buffalo Soldier**:**  I generally defragment twice before any attempt to partition.

Mustard**:**  I am using a CD that arrived in the mail, so no download errors.

Everyone**:**  Where on the install cd is the option to choose a partition to install into, if I have already partitioned the hard drive with something like Partition Magic?

Thanks again, everyone.

---

### Post by skinnygmg on 2006-04-22
i think mustard was refering to gparted live cd which sounds like it's OS independant (bootable) so it won't matter if you have linux up and running. (correct me if i'm wrong)  if that's the case, and it's a smaller file/download, go with that.

the new partition will probably show up in the list as a separate hard drive on thaat menu (i think)

---

### Post by babel on 2006-04-23
Here's what I did**:**

I tried to partition the disk with Partition Magic demo.  It was unsuccessful.  I decided that I had to shut down all running systems.  I shut down antivirus (AVG) and another program called Trojan Hunter.  Partition Magic would still not partition the disk.

I decided that my entire Windows 98 installation might be corrupted so I decided to reformat the disk & reinstall Windows 98 and then partition & install Ubuntu.  Well, I got as far as erasing the hard drive but couldn't reformat the hard drive to reinstall Windows.

No problem!  I'll just use the entire hard drive for Ubuntu.  I popped in the install CD.  The CD formatted the hard drive.  I installed Ubuntu - still in progress while I write.

I'll be back on the boards soon as I'm sure I'll have many questions.  But several related important questions now**:** (1) Does the default installation of Ubuntu contain a web browser?  (2) Where do I find it on the desktop?  (3) Should I unplug from the Internet until I install an antivirus program?  (4) If so, where do I find a linux antivirus program?  (5)  Do I need a software firewall like I did with Windows?  (6)  If so, where do I find one?

Thanking everyone for their help,

Babel.

---

### Post by gr0kzer0 on 2006-04-23
(1) Does the default installation of Ubuntu contain a web browser? (2) Where do I find it on the desktop?

The default install comes with Firefox. Applications > Internet > Firefox Web Browser

---

### Post by skinnygmg on 2006-04-23
[QUOTE=babel]
(1) Does the default installation of Ubuntu contain a web browser?
[/QUOTE]

yes. firefox

[QUOTE=babel]
(2) Where do I find it on the desktop?
[/QUOTE]

it will be a little globe icon next to the menu in the upper left corner

[QUOTE=babel]
(3) Should I unplug from the Internet until I install an antivirus program?
[/QUOTE]

no

[QUOTE=babel]
(4) If so, where do I find a linux antivirus program?
[/QUOTE]

there are several answers.  you can post/look for posts on that later

[QUOTE=babel]
(5)  Do I need a software firewall like I did with Windows?[/QUOTE]

no.  but a hardware firewall (router) would be a good idea

---

### Post by skinnygmg on 2006-04-23
antivirus info

clamav can be installed from synaptic (util used to find, install, and update software)

here's a howto on installing AVG for linux
[http://www.ubuntuforums.org/showthread.php?t=136064](http://www.ubuntuforums.org/showthread.php?t=136064)

---

### Post by babel on 2006-04-23
Thanks, everyone!

I have a hardware router so will use that as protection for now.

I'll look into clamav.

Now that I am finally installed I will put any further questions into new posts.

Thanks.

babel

---

### Post by garner_nc on 2006-04-23
I agree with BuffaloSoldier. I've had this same problem before. Usually can be corrected by running MS defrag in safe mode then re-booting and running your Linux install again.

All the Best,
Doug White
Garner, NC USA

---

