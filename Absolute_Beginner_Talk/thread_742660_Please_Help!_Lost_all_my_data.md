---
title: "Please Help! Lost all my data"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by elexhobby on 2008-04-01
Hello..

I wanted to copy data from a dvd.. However, it was giving input output error.. On googling, I learnt about dd_rescue.. So I typed in

sudo dd_rescue /dev/hdd /dev/hdb3

and all the previous files in a drive called hdb1 are deleted it seems, and it now contains files whose names are some random symbols like !z?r. I realized this immediately and aborted the dd_rescue in about 15 secs, but still my data in hdb1 seems to be lost. Also, the hdb1 drive is of size 80GB, however the total size of all those random files is around 1.5GB and free space being shown is 522MB, thus making the size of hdb1 as 2GB. How is that possible..

I guess I should have created a folder and created the backup in a folder.

Is there no way I can recover my old files in hdb1?

Please please help me.

---

### Post by c-ron on 2008-04-01
Don't reboot or power off if you haven't already!

Are you still reading?

---

### Post by elexhobby on 2008-04-01
Yes.. Please go on

---

### Post by c-ron on 2008-04-01
---

---

### Post by elexhobby on 2008-04-01
Thanks.. No I haven't rebooted.. Another weird thing.. When I simply right click on the drive and say properties, it shows 104GB full.. (I'm sorry the drive size is 105GB, not 80GB as I mentioned earlier).. I cant understand which files are occupying this memory. I even said show hidden files. Still, all the displayed files (those with random symbols) take only around 1GB, and yet the free space is only 500MB, not 104GB..

---

### Post by c-ron on 2008-04-01
It may be possible to recover your data. Don't reboot and don't write any more data to the drive. Do you have a second computer that you can get on IRC irc.ubuntu.com #ubuntu ?

---

### Post by elexhobby on 2008-04-01
I have another computer but it has Windows.. Does IRC mean something like real time chatting? I don't know how its used.. Can I chat with you using pidgin/gaim from this computer(ubuntu) itself?

---

### Post by c-ron on 2008-04-01
I wouldn't use that computer any more until you figure out a plan of action on how to recover the data. use the windows pc and connect to [http://java.freenode.net/](http://java.freenode.net/)

enter in your username: elexhobby and for the channel put ubuntu

---

### Post by c-ron on 2008-04-02
Sorry I couldn't help more...unfortunately.. some of your data was overwritten by dd_rescure with random bits... :-(  here's the info I was looking at that might get you on the right track to recover anything that's left:

1st, try doscfsck:

sudo dosfsck -a
[http://linux.about.com/library/cmd/blcmdl8_dosfsck.htm](http://linux.about.com/library/cmd/blcmdl8_dosfsck.htm)

If that doesn't work..

More on gpart:
[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

Rebuild a corrupted Partition Table the gpart/fdisk way

[http://www.cauniversity.org/node/344](http://www.cauniversity.org/node/344)

Recover lost partition table using Ubuntu Live CD + gpart
[http://www.mohdshakir.net/2008/01/03/recover-lost-partition-table-using-ubuntu-live-cd-gpart](http://www.mohdshakir.net/2008/01/03/recover-lost-partition-table-using-ubuntu-live-cd-gpart)

Keep trying the #ubuntu channel on irc.ubuntu.com if you need more help, and be sure to post here what the outcome is.

---

### Post by elexhobby on 2008-04-02
Thanks so much.. I'll try all these things out and let you know.. Btw, you had asked me to do sudo fdisk -l /dev/hdb3 >> ~/Desktop/fileinfo.txt.. It said /dev/hdb3 doesn't have a valid partition table.. Was that because /dev/hdb3 was unmounted?

Anyways, should I do gpart /dev/hdb3?

---

### Post by c-ron on 2008-04-02
That should be:

```
sudo fdisk -l /dev/hdb -l >> ~/Desktop/fdiskinfo.txt
```

Then run dosfsck...

---

### Post by aroustaei on 2008-04-02
hello 
maybe [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") can help you i have used it to recover my deleted partition before

---

### Post by elexhobby on 2008-04-02
Hi c-ron,

Here are the contents of fdiskinfo.txt after I ran 

sudo fdisk -l /dev/hdb -l >> ~/Desktop/fdiskinfo.txt

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27cd27cd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         122      979933+   5  Extended
/dev/hdb2             123        5227    41005912+  83  Linux
/dev/hdb3           16711       30401   109972957+   b  W95 FAT32
/dev/hdb4            5228       16710    92230488    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


I also tried dosfsck.. It doesn't scan.. I gives the following output.. 

sudo fdisk -a /dev/hdb3
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Logical sector size is zero.

I also tried sudo dosfsck -V /dev/hdb3, but it gave the same output..


Now I'm running sudo gpart /dev/hdb3.. However, the output as of now is just
Begin scan..

and its stuck at this for the past half n hour.. I'm not even sure if its scanning.. Am I doing right? Any suggestions?

@aroustaei: I havent yet tried testdisk.. Will try that if gpart fails..

---

### Post by elexhobby on 2008-04-02
Hi..

c-ron: the gparted is still stuck on Begin scan..

i tried testdisk.. but i don't know how to use it.. I asked it to analyse.. and after analysis, asked it to list contents of my crashed drive.. However, it doesn't show files that I had earlier stored there.. Could somebody please  point me or instruct me how to use testdisk in my kind of situation

---

### Post by c-ron on 2008-04-02
Here's a good page on using testdisk: [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

However, bad news. The dd command and dd_rescue are both data streamers, meaning they read data from one source and write it to another. The files that were overwritten are probably NOT recoverable without an expert involved. If the data that was lost is important, it's worth taking it to a specialist. Sorry I couldn't help. :-(

For anyone else reading this, don't use dd or dd_rescue in everyday operations. These tools are designed to fix specific issues and should not be used lightly.

---

### Post by elexhobby on 2008-04-03
Hi c-ron,

Thanks so much for all your help. 

The gpart took about 3 hours to scan. However, when I wrote the partition table returned by it, all my old contents were destroyed, and some 6 files from the dvd were copied instead. (I guess it copied them in those 15 secs).

I would have loved to have the data back, but I guess it isn't so important that I should hire an expert to get it back.

Anyways, the problem now is instead of the 105GB disk, it now shows a drive of 500MB containing those 6 files copied from the dvd. Do you still feel I could recover my data? If not, how do I format the drive and get a clean 105GB drive?

---

### Post by elexhobby on 2008-04-03
This is the entry that sudo fdisk -l gives me. 

I would like to recover the /dev/hdb3 drive. 

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27cd27cd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1           9       69016+   5  Extended
Partition 1 does not end on cylinder boundary.
/dev/hdb2             123        5227    41005912+  83  Linux
/dev/hdb3           16711       30401   109972957+   b  W95 FAT32
/dev/hdb4            5228       16710    92230488    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

When I tried gksudo gparted, it shows me the entire 232GB as unallocated.

---

### Post by nathansoz on 2008-04-03
If you are not able to recover your data, I would recommend using a partitioning utility to delete all partitions and then create a new partition spaning the entire drive. If this drive is shared with windows make the partition fat32 or ntfs (ntfs if 2000, xp, or vista) if not make it ext3.

UPDATE: Sorry I didnt see your last post. Do you have windows installed and on what partitions?

---

### Post by c-ron on 2008-04-03
Reboot with the LiveCD that you installed Ubuntu with. 
Run (ALT+F2) sudo gparted, select the /dev/hdb device from the drop down list in the upper-right corner.
Select (highlight) and delete the /dec/hdb3 partition. This will leave some free (unpartitioned) space on your drive. 
Write the changes and reboot the computer, remove the LiveCD and load Ubuntu.
Install the gparted program and the ntfsprogs package from Synaptic or: sudo apt-get install gparted ntfsprogs . 
Run: sudo gparted, select the /dev/hdb device again from the drop down list, select the free (unpartitioned) space, and create a new (formatted) NTFS partition.

---

### Post by elexhobby on 2008-04-03
Just wanted to confirm doing through the live cd, won't delete my old linux right and other drives? I mean /dev/hdb2 and /dev/hdb4 in the following table.. I only want to format /dev/hdb3.

This is the complete output for sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x200a2009

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1266    10169113+   c  W95 FAT32 (LBA)
/dev/hda2            1267        9732    68003145    f  W95 Ext'd (LBA)
/dev/hda5            1267        5090    30716248+   b  W95 FAT32
/dev/hda6            5091        7640    20482843+   b  W95 FAT32
/dev/hda7            7641        9732    16803958+   b  W95 FAT32
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27cd27cd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1           9       69016+   5  Extended
Partition 1 does not end on cylinder boundary.
/dev/hdb2             123        5227    41005912+  83  Linux
/dev/hdb3           16711       30401   109972957+   b  W95 FAT32
/dev/hdb4            5228       16710    92230488    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

---

### Post by c-ron on 2008-04-03
Please re-read my post above. I've made some edits to it.
If you only select the /dev/hdb3 partition to delete then your others should be fine.

---

### Post by elexhobby on 2008-04-03
Thanks.. Wii do as you said.. Just one question.. Will this make my new partition visible from windows? (installed on /dev/hda). (Earlier, it would not be visible from Windows, even though it was FAT32)... If not, how do I ensure it becomes visible from Windows? Do I need to partition from Windows, say using Partition Magic, or can it be done from Ubuntu itself?

---

### Post by c-ron on 2008-04-04
I could be mistaken, but I believe Windows has a problem seeing FAT32 partitions that are large than 40 GB. That is why I recommend formating as NTFS.

---

### Post by elexhobby on 2008-04-04
Hi,

I did as you said, and its the same problem. gparted doesn't show me 3 partitions on /dev/hdb at all. It shows me the complete 232GB (/dev/hdb is a 250GB harddisk) as unallocated. I'm attaching the image of the gparted screen. Why is this happening? What do I do?

---

### Post by c-ron on 2008-04-06
That's odd.. now what is the output of:
```
sudo fdisk -l /dev/hdb >> ~/Desktop/fdiskinfo.txt 
```

You might want to download and burn the LiveCD version of GParted and try again:
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

---

### Post by elexhobby on 2008-04-07
Hi..

These are the contents of fdiskinfo.txt

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27cd27cd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1           9       69016+   5  Extended
Partition 1 does not end on cylinder boundary.
/dev/hdb2             123        5227    41005912+  83  Linux
/dev/hdb3           16711       30401   109972957+   b  W95 FAT32
/dev/hdb4            5228       16710    92230488    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


Also, it said at the terminal - Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

What's gone wrong? Also, the drive in whcih the dvd contents have been copied (6 files).. Its become a read-only drive like a cd drive. I can't delete or write anything to that drive.

---

### Post by elexhobby on 2008-04-08
Also, the GParted I'm using, I downloaded it using Synaptic.

---

