---
title: "can I access dual boot linux data from OSX or Live CD"
date: 2006-09-21
forum: Apple PPC Users
---

### Post by goneskiing on 2006-09-21
The security update trashed my linux boot (with reFIT there is no rescue mode).  Since I have several days of data unbacked up - is there a way to get at my data from either OSX or a Live CD - I can't figure out how I can mount the Linux partition - can anyone help (with specific instructions).  Thanks.

---

### Post by zxee on 2006-09-21
If it's a linux partition-say an ext3 filesystem you should be able to mount with > sudo mount /dev/hdaX /mnt/hdaX
Note: the 'hdaX' is of course an example you would use whatever the actual partition designation is, and you have to create a directory in /mnt to mount to. Some people seem to use temp or something but I create a matching directory for the partition because it keeps things straight for me. So > sudo mkdir /mnt/hdaX is the command for my example to create a mount point. 
There is also a ext3 program for reading linux from OSX but that another story.

---

### Post by goneskiing on 2006-09-21
*sudo mount /dev/hdaX /mnt/hdaX*

on OSX there is no /dev/hdaX nor /dev/sdaX - there is a disk3, disk4 - when I tried to mount those I get a "busy" message

I'll try this from the live CD as well.

---

### Post by zxee on 2006-09-21
> **goneskiing said:**
> *sudo mount /dev/hdaX /mnt/hdaX*

on OSX there is no /dev/hdaX nor /dev/sdaX - there is a disk3, disk4 - when I tried to mount those I get a "busy" message

I'll try this from the live CD as well.

I meant using the live cd. I should have been more specific.

---

### Post by goneskiing on 2006-09-22
Thanks - I rescued the data via the Live CD and a flash drive.

---

### Post by zxee on 2006-09-22
For those who might be interested there is a program w/gui interface for mounting and reading ext2/3 fs in OSX (only works with 10.2-10.3) [http://freshmeat.net/projects/ext2fs/](http://freshmeat.net/projects/ext2fs/)

---

