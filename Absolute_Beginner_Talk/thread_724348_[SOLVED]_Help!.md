---
title: "[SOLVED] Help!"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-14
I think I may have put myself in trouble.

I just uninstalled my windows vista, this was my previous configuration:

sda1 - Windows vista (140G)
sda2 - Windows recovery (HP laptop) (10G)

sdb1 - Files etc in NTFS (130G)
sdb2 - Linux (at the end of the hard drive)

I then booted up with my ubuntu boot DVD, removed all partitions from sda1, and replaced it with a new ubuntu installation. This is the new configuration:

sda1  /                  ext3   13.8G
sda5  /home          ext3   131.1G
sdb5  /media/sdb5 ext3   15.9G

So somehow I cant find my previous sdb1 (see above),** I have a lot of important documents there - ** so i would really like to move these files into my sda drive and then remove all partitions from the sdb drive and convert that into ext file system as well.

My other question is:

because I left my old ubuntu on (sdb2) which is now called sdb5 - I now have 2 different versions of ubuntu on my boot menu when I start up the computer. How do I remove this ?

Can anyoneone help me plz?

best regards /Anders

---

### Post by sandysandy on 2008-03-14
> **lover_of_sc said:**
> 
So somehow I cant find my previous sdb1 (see above),** I have a lot of important documents there - ** so i would really like to move these files into my sda drive and then remove all partitions from the sdb drive and convert that into ext file system as well.

My other question is:

because I left my old ubuntu on (sdb2) which is now called sdb5 - I now have 2 different versions of ubuntu on my boot menu when I start up the computer. How do I remove this ?

Can anyoneone help me plz?

best regards /Anders

post output of sudo fdisk -lu

with respect to other question the menu.lst will have to be edited for ubuntu entry changing.

regards

---

### Post by amaroKer on 2008-03-14
Where have you looked for sdb?  I would try opening the Partition Editor and just examine the drives to see what partitions exist. The toggle between drives is in the top right corner.   If your partition shows up there, you just need to mount it.  You may be able to get to it through 'Computer' if this is the case.  If not, consult help on mounting partitions.

---

### Post by lover_of_sc on 2008-03-14
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29302559    14651248+  83  Linux
/dev/sda2        29302560   312576704   141637072+   5  Extended
/dev/sda5        33286680   312576704   139645012+  83  Linux
/dev/sda6        29302686    33270614     1983964+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   274838208   137419073    7  HPFS/NTFS
/dev/sdb2       274840020   308672909    16916445    5  Extended
/dev/sdb5       274840083   308672909    16916413+  83  Linux

---

### Post by amaroKer on 2008-03-14
> Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1              63   274838208   137419073    7  HPFS/NTFS**

Looks like your partition is still there, you just need to mount it.

---

### Post by amaroKer on 2008-03-14
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by lover_of_sc on 2008-03-14
Hmmm I have tried but I cant seem to get it right, how do i do that mate? Cheers for your assistance.

---

### Post by sandysandy on 2008-03-14
amaroKer is right. ur sdb1 NTFS (windows) partition is there.

go to Places -----> Computer  and have a look.

regards

---

### Post by lover_of_sc on 2008-03-14
yes I can actually see a sdb1 partition oin there but there are no files what so ever in it? sorry for being a pain

---

### Post by sandysandy on 2008-03-14
> **lover_of_sc said:**
> yes I can actually see a sdb1 partition oin there but there are no files what so ever in it? sorry for being a pain

right click the partition and see the properties of the partition.

that way u can make out how much of the partition is used and if the old files have chance of being there.

regards

---

### Post by lover_of_sc on 2008-03-14
i can only see below partions under system monitor:

/dev/sda1          /                 ext3           13.8 tot       10.6 free
/dev/sda5          /home         ext3           131.1tot       125.1 free
/dev/sdb5         /media/sdb5 ext3           15.9tot         7.6free


wierd? or am I just useless... hehe

---

### Post by sandysandy on 2008-03-14
as i pointed out in Post#8 above

go to Places -----> Computer and have a look. (Places menu is on title bar between Applications and System)

regards

---

### Post by lover_of_sc on 2008-03-14
I can find the folder sdb1 - but it;s emptey mate?

---

### Post by lover_of_sc on 2008-03-14
I think I made some break trough, i installed gparted and it found the hard drive - BUT it comes up with an error message:

Unable to read the contents of this file system! Because of this some operations may become unavaliable. 

How can it not read NTFS? it used to be able to do that?

---

### Post by amaroKer on 2008-03-20
Did you find your files?  How was your problem solved?

---

### Post by lover_of_sc on 2008-03-21
Hi mate, yes we managed to solve it in the end in tread 'http://ubuntuforums.org/showthread.php?t=725133'

Think there were several issues, for some reason sdb started on sector 63 instead of 1. I completely removed my windows, formatted sda into ext and reinstalled ubuntu on that partition. Moved all my files into sda1 and made that into ext as well. So now it's all working  and all my files are left intact! :-) Thanks to the very helpful and amazingly skillful linux community. 

happy easter!

---

