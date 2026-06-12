---
title: "Installation error"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Shimajiro on 2006-11-24
Good Evening,

Today I tried to install ubuntu on my laptop which has pre-installed XP on it. I got stuck at Step 6 of 7. I selected 1st option to prepare the disk space which automatically distributes the current disk space. However after a few seconds I got error saying "Enough diskspace could not be generated!" :( 

I have a 40GB harddisk with 15GB eaten up by XP and I see about 20GB as empty space.

Can anyone suggest what's wrong?? 

Thanks n regards,
Shi
....
Update: I tried to defragmate the disk to give it another try... however now I get the following error.....

Uncompressing Linux....Ok, booting the kernel
[17179582.252000] PCI: Cannot allocate resource region 4 of device 000:00:1d.0
[17179582.252000] PCI: Cannot allocate resource region 4 of device 000:00:1d.1
kill: Could not kill pid '3865': no such process
* INIT: Id "1" respawning too fast: disabled for 5 minutes
* INIT: Id "2" respawning too fast: disabled for 5 minutes
* INIT: Id "3" respawning too fast: disabled for 5 minutes
* INIT: Id "4" respawning too fast: disabled for 5 minutes
* INIT: Id "6" respawning too fast: disabled for 5 minutes
* INIT: Id "5" respawning too fast: disabled for 5 minutes
* INIT: no more processes left in this runlevel

pls help.....:confused:

---

### Post by Bartender on 2006-11-24
Are you using the LiveCD?
How much RAM do you have?  If less than (or very close to) 256 you should try the alternate install CD.
Did you download the .iso?  If so, did you check the md5 hash before converting to a bootable CD?

---

### Post by rlozano on 2006-11-24
and did you make a separate partition before installing ubuntu? although it can resize for you during the installation, there's no guarantee that your data will be saved.

you can try doing the installation again, by making a partition of your HD first in windows (as this is where you are familiar with, i guess).

---

### Post by kenweill on 2006-11-24
> **Shimajiro said:**
> 
I have a 40GB harddisk with 15GB eaten up by XP and I see about 20GB as empty space.


You cant install Ubuntu with 20GB free space. You need a free partition. Not free space.

Try adjusting your windows partition using Partition Magic(from windows) or Gparted(from the Live CD of Ubuntu). Make space.

Then try to install Ubuntu again.

---

### Post by Shimajiro on 2006-11-26
Thank you for quick replies friends. Here are some clarifications..

1. Yes, I am using a live CD. I have downloaded the iso image and created a live CD. No... I have not checked for md5 hash as I don't understand what it is.

2. I am aware of the partition requirements and as I mentioned in my question, I am getting this error during the partition stage only. I am using Gparted which comes with the ubuntu installation. I tried using the automatic as well as manual partiation step. However I am getting same error... "Enough Partition space could not be created". I tried it on another machine and had similar problem. only the "completely erase this hard disk" option seems to be working. *Is this a problem related to Gparted?*

3. I have enough RAM I guess, 752 MB ?????

Regards,
Shital

---

