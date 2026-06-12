---
title: "Reformatting hdb1?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-08-21
I currently have my hdb1 recognized as the 'storage' folder under Places>Computer>Filesystem.  How can I reformat hdb1?

---

### Post by hopstah on 2006-08-21
the way to format it varies depending on what filesystem you want to use.

to get ext3, it's ```
sudo mke2fs -j /dev/hdb1
```
to get ext2, it's ```
sudo mke2fs /dev/hdb1
```
to get fat32, xfs, reiserfs or reiser4, someone else will have to help you out.

edit:  i just re-read your post.  do you want to reformat it, or do you want to change what it shows up as?  to get it to show up as something other than storage, you need to change the mountpoint.  if that's what you need to do, i'll explain that, but to reformat, follow the instructions above.

and remember, reformatting means losing all of your data.

---

### Post by Guns90 on 2006-08-22
I'm not even sure how partitions work.  My hdb1 used to be my hda1.  It is loaded with 5.10 and files that I created back then.  I have everything I need from hdb1 copied over to hda1 now, so I would like to wipe hdb1 clean to use it for backing up data files from hda1.  What do you recommend that I do?

---

### Post by Guns90 on 2006-08-23
I tried the 'sudo mke2fs -j /dev/hdb1' command and got.....
gary@my-desktop:~$ sudo mke2fs -j /dev/hdb1
mke2fs 1.38 (30-Jun-2005)
/dev/hdb1 is mounted; will not make a filesystem here!
gary@my-desktop:~$

????

---

### Post by hopstah on 2006-08-23
yeah, sorry about that.  you first must unmount the drive.  and if this is your root drive (the drive that ubuntu is installed on) then you will have to boot into the livecd in order to complete this operation.

before unmounting, make sure that the drive isn't currently being accessed by any program, such as an audio program, or something else of the surt.  but in order to unmount the drive, simply type ```
sudo umount /dev/hdb1
```
and then you should be able to reformat it without a problem.

---

### Post by Guns90 on 2006-08-24
Sorry that I have to seek more help on this.  I look like a real idiot at this point, huh?  (Nevermind that; it's rhetorical.) 
 
I unmounted, sudo mke2fs -j /dev/hdb1, and mounted it (using sudo mount /dev/hdb1/).  When I access the storage file now I see that it has 0 items in 67.7 GB. This is an 80 GB drive.  13.3 GB seems (to me) to be a lot of disk space left unusable, but I'm sure that I can get by with this.  

I tried to copy (drag and drop) files from hda1, but I am being told that I do not have permission to write to this file. If I have permission to do everything in the preceeding paragraph, then (to me) I should have permission to do what I want in the clean file.  Again, I have to say ?????.

---

### Post by hopstah on 2006-08-24
ok, try this.  unmount the drive again, and also run ```
sudo umount /dev/hdb2
```then run ```
sudo fdisk /dev/hdb
```then enter 'd' to delete a partition, and enter '1'.  hit 'd' again to delete another partition and hit '2'.  do this until it tells you there are no more partitions to delete.  then hit 'n', then 'p', and hit enter to use the entire drive space.
hit 'w' to write the changes to the drive.  then do ```
sudo mke2fs -j /dev/hdb1
``` to reformat the entire drive as ext3.  what you should have just done is delete any secondary partitions on the drive and then create one partition which uses up the entire drive, and then make it an ext3 partition.

(also, remember that when hard drives are sold, they define a gigabyte as 1 billion bytes, when a gigabyte is actually 1.0737 billion bytes, which means that every hard drive you buy is going to be approximately 7% smaller than advertised.)

ok, now that that is done, you want to change the permissions of the drive so that you can drag and drop to the drive.  right now, the drive is owned by root, and not by you.  to change that, execute ```
sudo chgrp *username* -R /mount/point/of/dev/hdb1
sudo chown *username* -R /mount/point/of/dev/hdb1
```
now the drive is owned by you, and you can do whatever you want.
if you want to copy a bunch of stuff, it's better to use the 'rsync' command.  you may need to ```
sudo apt-get install rsync
``` but i don't remember.  so, for example, if you have your /dev/hda1 mounted as /media/hda1 and your /dev/hdb1 mounted as /media/hdb1 and you want to copy EVERYTHING from /dev/hda1 to /dev/hda2, execute this in a terminal ```
rsync -aS /media/hda1 /media/hda2
``` and let it do it's thing.
i hope this helps.

---

