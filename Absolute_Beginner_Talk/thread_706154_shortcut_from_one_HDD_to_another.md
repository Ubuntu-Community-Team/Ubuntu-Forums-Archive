---
title: "shortcut from one HDD to another"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2008-02-24
I have 2 HDD's in my pc:

1. 300G which has the OS on it and music files
2. 500G 

I have more than 300G of music so I would like to have a link on the 1st 300G drive that will take me to a directory on the 2nd HD so that I can split up my music files over both disks.

I did a search and came up with a symlink but I have no idea if this is the best way to do it and indeed how to do it  :confused:

Any help appreciated.

---

### Post by anagor on 2008-02-24
Soft symbolic link is the best and easiest way to do it, I believe, and its the common way in Linux for such things.
If you are using Gnome , you can right-click on the folder that you want to link, choose "make link", this will create a link named "Link to somefolder", than you can just copy or move this link to a place where you want it to be, for example in /home/me/my music/.
also you can rename the link to something more appropriate.
of course there is a faster and easier way in console to do it:
open up a terminal and write something like this;

ln -s /media/MY_OTHER_DISK/Music /home/my_home/Music/from_other_disk

this will create a symbolic "soft" (the only possible between different partitions/disks) link in your home directory that points to the other disk/directory.

---

### Post by carverj on 2008-02-24
Hi there, could you please elaborate a little on your setup.
What is on the second hard drive?
If there is a file system on there such as windows or linux, then you would create a mount point to it on your 300G linux disk. I find the best way to do this is to create a mount point in the file /etc/fstab.
I hope this is a step in the right direction!

---

### Post by fast eddie on 2008-02-24
I am using Clark Connect, and I know this is an Ubuntu forum but I have had very helpful advice here in the past so I thought I would ask here again ;)

I am running it as a headless server for my SB3. 

The 2nd HD I have formatted for ext3 and is empty at the moment.

Bit confused as to what the paths are for the command: ln -s /media/MY_OTHER_DISK/Music /home/my_home/Music/from_other_disk

on the 1sd HD the files are stored here: /media/SB3 Files and the 2nd HD I have mounted it here /mnt/HardDrive/SB3 Files cont

Bit confused as to which path goes where in the above command line

Hopefully that makes sense :confused:

Is there a command I can use to show how much free sppace there is on each of the drives as well?

Thanks for the help - it is very much appreciated,

Graham

---

### Post by carverj on 2008-02-24
> Is there a command I can use to show how much free sppace there is on each of the drives as well?

try the command:
df

it stands for disk free (man df)
if unsure of a command again just type:
 apropos disk free (for example)

> Bit confused as to what the paths are for the command: ln -s /media/MY_OTHER_DISK/Music /home/my_home/Music/from_other_disk

on the 1sd HD the files are stored here: /media/SB3 Files and the 2nd HD I have mounted it here /mnt/HardDrive/SB3 Files cont

Bit confused as to which path goes where in the above command line


hmm. try ln -s /mnt/HardDrive/SB3\ Files\ cont /home/{username}/Desktop

---

