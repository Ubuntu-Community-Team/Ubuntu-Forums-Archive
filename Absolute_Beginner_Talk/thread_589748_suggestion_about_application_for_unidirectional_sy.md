---
title: "suggestion about application for unidirectional synchronization"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by g.a. on 2007-10-24
Hi,

I'm asking a suggestion about a possible application to perform unidirectional files synchronization.

I have my laptop with kubuntu 7.04 with all my personal files under $HOME/data

I made a copy of the directory on an external hard disk.

Once a week I just want to update the hard-disk. Since they are 6 GB of data I would like to avoid erasing and copying again the data but only update the modifications.

Any hints?

Thanks in advance,
g.

---

### Post by hyper_ch on 2007-10-24
how about rsync?

I also made a nice little script for auto-updates on my computer ;)

---

### Post by vanadium on 2007-10-24
That is indeed the one application. For local "mirroring", you want to use the option -a. In addition, if you checked all goes well, you want files that you deleted in the source to be deleted in the destination as well with the option --del. Thus, your command will look like

rsync -av --del $HOME/data /media/mydisk/data

where you obviously should substitute the correct path instead of /media/mydisk/data.

For convenience, you can put this line in a text file with the name bkdata (or another name of your choosing). Add #!/bin/bash as the first line and make the script executable. Now, you can perform the backup with the simple command ./bkdata. If you put the file in a directory that is in your path, then you can call the script wherever you are with the command bkdata.

Warning: add the --del option only after you tested that the copy goes to the right destination. If you swap source and destination, then your "source" would be wiped clean if destination did not yet contain anything!

---

### Post by g.a. on 2007-10-24
that's what I need, thanks a lot.
g.

---

### Post by hyper_ch on 2007-10-24
it even works over a ssh connection to a remote box if needed...

---

### Post by g.a. on 2007-10-25
I made all the steps suggested. thanks again.

I made several tests and all seems to work 'quite' perfectly for approx 6 GB of data.

however two small problems arise:

- if the only change in one source's file concerns its permission this is not propagated to the destination file (I just changed one single file from being executable to not);

- I receive plenty of error messages (almost for every file encountered) but the command seems to work perfectly. it is not comfortable to receive messages as:

rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

when backupping the personal data. I googled for this and I'm not sure about the reason for that. In one post it is stated that the reason is caused for the external device being formatted as fat32.

Does someone can clarify those two points to me?

again, thanks in advance,
g.

---

### Post by hyper_ch on 2007-10-25
The FAT32 is the source of your permissions problem. Fat32 doesn't use linux file permissions so the file "did not change".

well, if you have a browser open and surf the net during the sync, then the cache files with change and some will vanish. That could be a reason for that error OR when the user that you use to exectue rsync does not have proper permissions for a file.

---

### Post by g.a. on 2007-10-26
ok, thanks, this explains also the reason why copying files from winxp (ntfs) to an external usb hard rive (fat32) and then to linux make them appear as executable?

I used rsync as user and as root and without using the PC (all applications closed) and the error messages still is there, I tried the --modify-window=1 option (read somewhere) but nothing changed.

The fact is that all the files are correctly copied. I wonder if I can trust in this method as bk of my personal files.

g.

---

### Post by hyper_ch on 2007-10-26
well, I'd back them up onto an Ext3 formated storage device.

---

### Post by g.a. on 2007-10-26
well, I'm not so expert..., I have only two hard-disks, the laptop one and an external one of 75GB where I have several backups (both winxp and linux files). I used windows for the last 10 years and moved definitively to linux two weeks ago, several PC at work use windows so I need to store my files in a windows-compatible way.

Does winxp can read a ext3-formatted hard-disk?

In case it does not, can I partition my external hard-disk, one part in fat32 and the other in ext3? I made the partitions only under winxp using partition magic, in case this is a good solution could you suggest the command to use ?

thanks in advance,
g.

---

### Post by hyper_ch on 2007-10-26
You can partition it... I did so with my USB stick so that I have a bootable DSL on it and fat32 for the normal use ;)

There are drivers for windows to write to ext2/3 - but I never tested them.

---

### Post by g.a. on 2007-11-05
well, I have just partitioned my external hard-drive with gparted, some fat32 and some ext3 filesystems.

now I made as suggested a batch file where with rsync i update my personal files on the ext3 partition.

it works fine, thanks to all

g.

---

