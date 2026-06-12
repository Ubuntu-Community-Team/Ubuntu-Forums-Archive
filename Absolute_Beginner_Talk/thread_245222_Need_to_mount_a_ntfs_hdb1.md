---
title: "Need to mount a ntfs hdb1"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by garitd on 2006-08-27
ok heres my deal.  I have 2 hdd one is a 120GB full on ubuntu master.  The other is a ntfs slave that shows up in the computer as "G-Blayd" I have never been able to access this drive at all.  I read some things here and there and tried to edit fstab.. this is what mine looks like now after adding this line **

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
**/dev/hdb1	/media/blayd	ntfs	
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


basiaclly i dont know what im doing.  I dont use windows anymore.  (its a vow iv taken to help me really learn this stuff so far im pleased with my choice)  so its not important to keep the ntfs but I do have alot of music and pictures on the drive I dont want to lose...

so whats the best thing to do?  convert the drive to another file system?  or am I close to having this mount right?  If I click on the drive right now it says 

" Unable to mount the selected volume.

mount: only root can mount /dev/hdb1 on /media/blayd "

truthfully.. I dont know what im doing?  Where should this really be pointed to?

thanks for the help you guys rule!

-G-

---

### Post by Bachstelze on 2006-08-27
[Here](https://help.ubuntu.com/community/MountingWindowsPartitions) you go :)

---

### Post by garitd on 2006-08-27
oh man that was fast and you guys rock!  Thanks again!  

if anyone wants to know I added the /dev/hdb1 to the pmount.allow file and then double clicked the drive then closed the window and opened it back up and it works like magic.  

Today is a good day for Ubuntu!

-G-

---

