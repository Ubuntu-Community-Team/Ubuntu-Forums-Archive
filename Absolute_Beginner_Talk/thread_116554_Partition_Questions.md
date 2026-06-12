---
title: "Partition Questions"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by Bghmsh on 2006-01-13
Having Multiple OS's on my system i would like to delete the  partion that the PClinux system is on , how do i Identify the partition that Ubuntu resides on ??

---

### Post by benplaut on 2006-01-13
post the output of 'df -h', from your Ubuntu installation

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=Bghmsh]Having Multiple OS's on my system i would like to delete the partion that the PClinux system is on , how do i Identify the partition that Ubuntu resides on ??[/quote] 
Boot into Ubuntu. go to APPLICATIONS > ACCESORIES > FILE MANAGER

When the file manager opens, in the left hand pane, click on FILESYSTEM, go to the etc directory, inside the etc dir, there is a file called " fstab ". 

right click, open w/ Text editor. 

Look for a line 

/dev/hda3       /               ext3    defaults

the 2nd section with the lone " / " is your ubuntu root directory, and in this ( my ) case it is the 3rd partition of the 1st harddrive.

also note any other ext2, ext3, reiserfs, or other linux type partitions.

ignore the vfat, dos, or other windows formats.

one of the other linux partions is where your PClinux is installed. 

Hope this helps. If not I will be here for a while.

IF anyone else has better help to offer, please do so as I am new to offering help for linux users.

---

### Post by Jimmey on 2006-01-13
I think a simpler way would be 
```
sudo fdisk -l 
```

Hope that helps :P

---

