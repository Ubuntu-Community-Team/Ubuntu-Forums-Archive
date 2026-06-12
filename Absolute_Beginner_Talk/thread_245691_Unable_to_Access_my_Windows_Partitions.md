---
title: "Unable to Access my Windows Partitions"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by yossarain on 2006-08-28
I am not able to access my window partitions. I have tried following the instructions given at this website :

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

After typing "sudo fdisk -l" this is what my output is

[I][B]Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        8566    59038875    f  W95 Ext'd (LBA)
/dev/hda3            8567        9729     9341797+  83  Linux
/dev/hda5            1217        4864    29302528+   b  W95 FAT32
/dev/hda6            4865        8512    29302528+   b  W95 FAT32
/dev/hda7            8513        8566      433723+  82  Linux swap / Solaris[/B][/I]

Continuing further after typing "sudo nano /etc/fstab" the output is like this

[B][I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0[/I][/B]

which is entirely different from what is shown during the instructions. As i see it, i have two drives for cd one CD R/w and One for DVD. But the above output is showing only one cdrom0.

It is here i have stopped doing any further changes as is suggested in the original website fearing any change might harm my hard disks.  To make the things clear I have three partitions under Windows, C, D, E. C is where Windows XP is (NTFS), D and E are just for storing other information which are in FAT format. 

Please help me for further instructions. I am a newbie so command line instructions with explanation would be welcome as to what to type .

---

### Post by catlett on 2006-08-28
The fdisk output is the view of your partitions. /etc/fstab is the file that tells the system which partitions/drives to mount on startup. 
As you can see, your winddows partition /dev/hda1 is not listed in /etc/fstab and therefore you cannot access it. You have to add an entry in /etc/fstab for that partition. So enter ```
gksudo gedit /etc/fstab
``` (nano is a little complicated for my liking but use whatever editor you want)
add this line to the end of the file ```

/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```
Save the file and close. Now you just have to make a place for the partition to be mounted to. I put the mount points in media because that will give you an icon on the desktop and it is where ubuntu mounts drives as well. So enter 
```
sudo mkdir /media/windows
```
So now you have an entry for windows partition and you have created the mount point. You can reboot for the changes to take effect or you can enter```
 sudo mount -a
```

---

### Post by yossarain on 2006-08-28
worked like a charm, thanks a zillion Carlett..

now if only you can give me further instructions on how to get the other partitions namely D and E (in windows) which are in FAT32 format to get to work.

ps: i am sorry if i sound snobbish but having "windows" drive on my desktop when i so much want to detach from it and embrace linux isn't to my liking. Is there any way i can have it on just Places->Computer..

---

### Post by yossarain on 2006-08-28
waiting for the reply on going to help.wiki.communities i landed up here with a detailed explanation on what to do but alas he leaves me totally confused

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Between Step 3 and Step 4 things change rapidly. When he says to follow the suit and append all the hard disks the same way he shows me the following thing:

[I][CENTER]
# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
/dev/hda1
/dev/sdb3
/dev/sdd1
/dev/hda2
[/CENTER][/I]

Now if only he could have explained why he did that as clearly the output screen above him has nowhere "sdb" in it and that's where i am stuck. Now i have to figure out if my disks are SATA or PATA type. I don't know how. will it not do if i just say

[I][CENTER]
/dev/hda1
/dev/hda2
/dev/hda3
/dev/hda5
/dev/hda6[/CENTER][/I]

Now again i am stumped to understand which are my two other HARD DISK PARTITIONS AMONG THE FOLLOWING: 

[I]Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        8566    59038875    f  W95 Ext'd (LBA)
/dev/hda3            8567        9729     9341797+  83  Linux
/dev/hda5            1217        4864    29302528+   b  W95 FAT32
/dev/hda6            4865        8512    29302528+   b  W95 FAT32
/dev/hda7            8513        8566      433723+  82  Linux swap / Solaris[/I]

Why is it that life is so complicated to get some basic things done in UBUNTU? is this how all the linux distros are or is it the case with UBUNUTU which i was utterly fascinated on seeing it. Now the next task for me once this is done would be how to play my  music files...well before that could someone please answer my quiries...

---

### Post by catlett on 2006-08-28
Here is a quick explanation of /etc/fstab [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
Usually ubu8ntu's installer will mount your other partitions but it didn't seem to work for you. 
Anyways here is what to do. Open up /etc/fstab again
```
gksudo gedit /etc/fstab
```
Add these 2 lines to it
```
/dev/hda5 /media/windowsD vfat iocharset=utf8,umask=000 0 0
/dev/hda6 /media/windowsE vfat iocharset=utf8,umask=000 0 0
```
Save the file and close. Now make 2 new mount points for the partitons. (you can use any name you want. I just picked windowsD and windowsE to have something that shows what it is but it can be anything you want. Just make sure you have it as your /etc/fstab mount point as well)
```
sudo mkdir /media/windowsD
```
```
sudo mkdir /media/windowsE
```
Reboot or do sudo mount -a

P.S. /dev/hda1 is your windows partition with the actual install of windows.
/dev/hda2 is a primary partition that is "hosting" 2 other partitions. To exceed the 4 primary partition limit, ectended and logical partitons were created. In youir case hda2 is an extended partition. Inside of that extended partition is 2 partitions hda5 and hda6. As far as mounting, you do not have to mount the extended partition. You mount the logical partitions as if they were primary partitions. FYI...There can only be 4 primary partitions. They will be listed hda1,2,3 and 4. Logical partitions' labeling starts at hda5. Even if you only had 2 primary partitoons hda1 and hda2, the logical partiton would be labeled hda5. The other 2 labels will not be given to a logical partitioon even if there isn't another primary partition.

---

