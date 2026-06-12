---
title: "Stuffed up making new /home partition, help please."
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2006-12-11
I've tried to make a new /home folder on an external drive that had loads of room on it.  The drive was formatted as NTFS but i made a new 100Gb partition and formatted it to FAT32 as I want to share the data between Ubuntu and Windows.

I've followed this [ how to ]( http://www.psychocats.net/ubuntu/separatehome) and now have trouble logging on.

At the log-in prompt I get the following message (I can't be exact because the font is miniscule...still having trouble with ATI drivers)

" Users $HOME /.dr*** file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.
Users $HOME directory must be owned by user and not writable by other users."

So, I seem to have stuffed up on permissions somewhere but I can't get passed the log-in prompt to have a look at anything.  No doubt I've got to CHMOD something or other but Im not sure what, where and how to get at it.

Help please. :(

---

### Post by taurus on 2006-12-11
Sorry to tell you but you can't have /home on a fat32/vfat!!!  It has to be at least ext2/ext3 because of permission problem.

---

### Post by Phosphoric on 2006-12-11
Ohhhh :-k

---

### Post by taurus on 2006-12-11
If you want to share data between Windows and Ubuntu, create a partition and format that as fat32/vfat.  However, you can read and write to Linux from Windows with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by Phosphoric on 2006-12-11
The idea of this project was to generate more space for Ubuntu to grow.  I found 10Gb of space on my original Windows hard drive and I'm worried that Ubuntu will rapidly run out of space, hence the idea to set up a 100Gb partition on my external drive.  Should i perhaps re-format that 100Gb partition in to two, one ext3 for the home folder and Fat32 for shared files?

To do any of this I need to regain access to Ubuntu.  I caried out the fateful deed using gparted on the live CD so I presume I will be able to reverse what I've done. ( I did back up my old home folder as advised in the howto)

Thanks

---

### Post by Phosphoric on 2006-12-11
Oh no, now I've made it even worse.

In trying to recover my old home folder, following the aforementioned how to I misstyped a line or something and it seems as if I have directory after directory copying themselves on top of each other until the disc is full.

In windows I would know how to drill down and remove the duplicate directories and files but I've lost the plot in Ubuntu and panic mode has set in.  I really don't want to reformat and start again, it's taken me a couple of months of battling to get a half decent working set up.

Could somebody please tell me how to post the text in the terminal and then help me recover my situation please?  I'm in a right mess. :-| 

Thanks

---

