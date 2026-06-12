---
title: "Urgent: Can't Log In and Need to Save Old Data"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by e123 on 2007-08-04
Hi All,

Today I changed my /etc/environment file (I added a JAVA_HOME) directory. When I rebooted, my ubuntu 7.04 installation logged me right off. I got that you were logged in for less than 10 seconds error message.

I can only log in via the failsafe terminal. When I attempt to take a look around and use a command like 'ls' it tells me the command is not installed and try 'sudo apt-get' of course sudo isn't there as well.

I can get the installation disk up and running, but I am not sure how to set my partitions so as not to lose my old /home directory.

What is my best strategy for saving my old data and reinstalling ubuntu?

Thanks in advance,
e123

---

### Post by TBerben on 2007-08-04
Do you have a separate partition for /home? If so, you can reinstall ubuntu without losing your data, in the partitioner choose manual, format your current /-partition and use it as / again. Mount your files partition as /home without formatting.

If you don't have a separate /home partition you can try booting a livecd and use that to move your files to another medium

---

### Post by Brunellus on 2007-08-04
> **e123 said:**
> Hi All,

Today I changed my /etc/environment file (I added a JAVA_HOME) directory. When I rebooted, my ubuntu 7.04 installation logged me right off. I got that you were logged in for less than 10 seconds error message.

I can only log in via the failsafe terminal. When I attempt to take a look around and use a command like 'ls' it tells me the command is not installed and try 'sudo apt-get' of course sudo isn't there as well.

I can get the installation disk up and running, but I am not sure how to set my partitions so as not to lose my old /home directory.

What is my best strategy for saving my old data and reinstalling ubuntu?

Thanks in advance,
e123
use the Live CD, mount the affected partition, and save the data you can by moving them to another drive--I keep a big fat removeable hard drive handy for just such emergencies.

Alternatively, you can save the partition that contains /home;  reinstall onto another partition, mount the old partition and do that.

---

### Post by e123 on 2007-08-04
? How do I use livecd to move my files to another medium? I have it installed

When I go into the terminal and look in the /home directory the only folder I see is ubuntu. I only see /home/ubuntu and not /home/e123

What am I missing?

---

### Post by Brunellus on 2007-08-04
the key step here is mounting all your partitions.  

Have a look at this page on the wiki:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29%7C%28partitions%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29%7C%28partitions%29)

---

### Post by e123 on 2007-08-04
> **Brunellus said:**
> use the Live CD, mount the affected partition, and save the data you can by moving them to another drive--I keep a big fat removeable hard drive handy for just such emergencies.

Alternatively, you can save the partition that contains /home;  reinstall onto another partition, mount the old partition and do that.

How do I identify the portion that contains my old /home? When I do, how do I mount it?

Thanks!

---

### Post by sdowney717 on 2007-08-04
[http://ubuntuforums.org/showthread.php?t=517262&highlight=live+cd+mount+partition](http://ubuntuforums.org/showthread.php?t=517262&highlight=live+cd+mount+partition)

try this, see boot live cd 
then mount your ubuntu partition

sudo fdisk -l lists all your partitions

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15260   122575918+   7  HPFS/NTFS
/dev/sda2           15261       24133    71272372+  83  Linux
/dev/sda3           24134       24321     1510110    5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris


mine would be /dev/sda2 for my ubuntu partitions

---

### Post by e123 on 2007-08-04
Ok

Thank you all for your quick help. I feel I am getting close to a save here!

sudo fisk -l 

gave me list of all the partitions

sda1 is where my home directory is.

I tried

sudo mount /dev/sda1 /mnt

and the command did not report a failure so I assume the partition is mounted. Now...where is it? If it mounted I can't find where to access its contents.

e123

---

### Post by e123 on 2007-08-04
got it now, read the post pertaining to the script.

ls /mnt I can also access it by going to the graphical user interface also. and finding the /mnt folder.

Thank you all!

---

