---
title: "NTFS harddrives are not on the desktop upon booting"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-01-18
I have 3 hard drives in my computer.  The only one that Ubuntu picks right up is the drive that it is installed on.  Every time I boot I have to go into "Computer" and double-click on them to put them on the desktop.  How can I keep them on the desktop for every time Ubuntu boots?

---

### Post by thedon_1 on 2008-01-18
I have the exact same problem, i hope someone knows what the solution is

---

### Post by forestpixie on 2008-01-18
can you post the ouput of these from terminal

sudo fdisk -l
cat/etc/fstab

---

### Post by jken146 on 2008-01-18
> **forestpixie said:**
> can you post the ouput of these from terminal

sudo fdisk -l
cat/etc/fstab

Just a slight correction: ```
sudo fdisk -l
```and ```
cat /etc/fstab
```

---

### Post by thedon_1 on 2008-01-18
Looks like the same problem here.

[http://ubuntuforums.org/showthread.php?t=669962&highlight=mount+ntfs](http://ubuntuforums.org/showthread.php?t=669962&highlight=mount+ntfs)

I'm about to try this now, i will post my result

---

### Post by thedon_1 on 2008-01-18
Yep, it worked!

Only thing is i kept the mount point as "mountpoint" and now i can;t delete that folder and use one with a better name. it says i do not have permision.

Any ideas on how to do it? I assume it will haev to be through terminal.

---

### Post by forestpixie on 2008-01-18
you'll have to remove the directory and make a new with a 'better' name

sudo mkdir /media*name*

sudo rmdir /media/*oldname*

and edit the fstab to suit the new name

```
gksudo gedit /etc/fstab
```

---

### Post by ladybumavere on 2008-01-18
> **jken146 said:**
> Just a slight correction: ```
sudo fdisk -l
```and ```
cat /etc/fstab
```


Output of "sudo fdisk -l"
```
Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d622d61

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hdb2            3188       19457   130688775    f  W95 Ext'd (LBA)
/dev/hdb5            3188       14150    88060266    7  HPFS/NTFS
/dev/hdb6           15124       19457    34812823+  83  Linux
/dev/hdb7           14637       15123     3911796   82  Linux swap / Solaris
/dev/hdb8           14151       14636     3903763+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed307f26

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdd: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0ade0ad

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       15016   120615988+   7  HPFS/NTFS

```


output from "cat /etc/fstab"
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc6
UUID=f00eea55-4e2d-49d3-bc45-d1846e2f7e9e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc8
UUID=43e1ca65-f33c-4df6-baa7-217c5bde3fa6 /boot           ext3    defaults        0       2
# /dev/hdc1
UUID=ECA4D6F6A4D6C1EE /media/hdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdc5
UUID=54ECEC5DECEC3ABE /media/hdc5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdc7
UUID=e41e4c6a-0ea0-4580-aa10-6d9c46069cfd none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```


Hope that helps!

---

### Post by forestpixie on 2008-01-18
can you do 

```
blkid
```

---

### Post by ladybumavere on 2008-01-18
> **forestpixie said:**
> can you do 

```
blkid
```


Yes sir!

```
/dev/hdc1: UUID="6E54E50954E4D4BD" TYPE="ntfs" 
/dev/hdb1: UUID="ECA4D6F6A4D6C1EE" TYPE="ntfs" 
/dev/hdb5: UUID="54ECEC5DECEC3ABE" TYPE="ntfs" 
/dev/hdb6: UUID="f00eea55-4e2d-49d3-bc45-d1846e2f7e9e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb7: UUID="e41e4c6a-0ea0-4580-aa10-6d9c46069cfd" TYPE="swap" 
/dev/hdb8: UUID="43e1ca65-f33c-4df6-baa7-217c5bde3fa6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdd1: UUID="C67CAE0A7CADF579" TYPE="ntfs" 

```

---

### Post by ladybumavere on 2008-01-18
Also, hdc1 and hdc5 are the ones that are on the desktop upon booting.

---

### Post by forestpixie on 2008-01-18
looks a  bit very confusing :)

if you've got hdc5 on the desktop I don't know where it's coming from as you only have hdc1 as far as fdisk reports and it shouldn't exist 

the hdb's and hdc's appear to be mixed up but with the correct UUID, while the important bit is the UUID the rest needs to be looked at carefully - eg 

> /dev/hdb1: UUID="ECA4D6F6A4D6C1EE" TYPE="ntfs" from blkid
> 
# /dev/hdc1
UUID=ECA4D6F6A4D6C1EE /media/hdc1 from your fstab

I've got to go now - had an exam today followed by 4 hours mucking about with win2k and my head hurts 

really don't want to muck that up for you - if no-one else drops by to look I will in the morning

---

### Post by forestpixie on 2008-01-19
the ones on the desktop are labelled hdc1 and hdc5 - is that right, about 24 and 83 Gb respectively and you have 3 or more Gb of swap.

Need to check that - and I'm assuming that you can boot into ubuntu ok

Edit - also can you post result of ```
ls /media
``` 
and the last portion of this command, after where it says
> ## ## End Default Options ##

```
cat /boot/grub/menu.lst
```

---

### Post by ladybumavere on 2008-01-20
> **forestpixie said:**
> the ones on the desktop are labelled hdc1 and hdc5 - is that right, about 24 and 83 Gb respectively and you have 3 or more Gb of swap.

Need to check that - and I'm assuming that you can boot into ubuntu ok

Edit - also can you post result of ```
ls /media
``` 
and the last portion of this command, after where it says


```
cat /boot/grub/menu.lst
```



Yep Yep.

```
ls /media
```
> cdrom  cdrom0  disk  floppy  floppy0  hdc1  hdc5  Local Disk

and
```
cat /boot/grub/menu.lst
```
> ## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,7)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=f00eea55-4e2d-49d3-bc45-d1846e2f7e9e ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,7)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=f00eea55-4e2d-49d3-bc45-d1846e2f7e9e ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,7)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by forestpixie on 2008-01-20
We'll make a backup first then open the file to edit it
```

sudo cp /etc/fstab /etc/fstab.2001
gksudo gedit /etc/fstab
```

add these lines to bottom of file
```

#/dev/hdd1
UUID=6E54E50954E4D4BD /media/hdd1 ntfs    defaults,umask=007,gid=46 0       1
#dev/hde1
UUID=C67CAE0A7CADF579 /media/hde1 ntfs    defaults,umask=007,gid=46 0       1

```

save the file and close gedit

in terminal do these one at a time
```

sudo mkdir /media/hdd1
sudo mkdir /media/hde1
```

then 
```
sudo mount -a
df -h
```
the last command should now show all your partitions, I'm not sure about the 200Gb drive - I've read there have been a few problems - if it is post back on that

restart to make sure all works - if you get a problem when booting and get sent to a prompt - restore the backup with this command
```

sudo mv /etc/fstab.2001 /etc/fstab
``` and reboot which I think is
```
reboot
```

Hope that gets it done - understand why the numbering is all off now - it's got the cdrom as hda consequently the rest moved on one - no idea why though. I've carried on in the same manner so hopefully it'll make sense later for someone else.

Perhaps if someone else is looking they'll have some idea about that.

---

### Post by ladybumavere on 2008-01-20
> **forestpixie said:**
> We'll make a backup first then open the file to edit it
```

sudo cp /etc/fstab /etc/fstab.2001
gksudo gedit /etc/fstab
```

add these lines to bottom of file
```

#/dev/hdd1
UUID=6E54E50954E4D4BD /media/hdd1 ntfs    defaults,umask=007,gid=46 0       1
#dev/hde1
UUID=C67CAE0A7CADF579 /media/hde1 ntfs    defaults,umask=007,gid=46 0       1

```

save the file and close gedit

in terminal do these one at a time
```

sudo mkdir /media/hdd1
sudo mkdir /media/hde1
```

then 
```
sudo mount -a
df -h
```
the last command should now show all your partitions, I'm not sure about the 200Gb drive - I've read there have been a few problems - if it is post back on that

restart to make sure all works - if you get a problem when booting and get sent to a prompt - restore the backup with this command
```

sudo mv /etc/fstab.2001 /etc/fstab
``` and reboot which I think is
```
reboot
```

Hope that gets it done - understand why the numbering is all off now - it's got the cdrom as hda consequently the rest moved on one - no idea why though. I've carried on in the same manner so hopefully it'll make sense later for someone else.

Perhaps if someone else is looking they'll have some idea about that.



Every thing seemed to go fine and I had no problem booting, but they're still not on my desktop.  Odds are this is why.

When i did the command```
sudo mount -a
```this is what it reads...> Failed to access '/dev/disk/by-uuid/6E54E50954E4D4BD': No such file or directory
Failed to access '/dev/disk/by-uuid/C67CAE0A7CADF579': No such file or directory


I have a feeling that has something to do with it.

Thanks again for all the help!

---

### Post by Desperate on 2008-01-23
Hello, please don't stop here, I was learning :) My trouble so far running live CD so no grub, but I'm getting closer to solve my mishap.
Got her running again, ladybumavere ??

Thanks so far
Richard

---

### Post by kinkyHelenMandarin on 2008-01-23
I'm not sure if anyone suggested it,
but ntfs support is not there by default,
u need to install ntfs-3g drivers (u'll find it in Synaptic):
[http://www.ntfs-3g.org/support.html](http://www.ntfs-3g.org/support.html)

Edit: no, sorry, I think there is ntfs support by default, but just for reading, anyway ntfs-3g works for me.

---

### Post by Desperate on 2008-01-23
Hi got that part but haven't read that page yet. Installed it, but as I have a ntfs ata raid0 I need another approach, getting closer every day, but very slow :) Gotta read a lot to find out what and how, Thanks for the help
Richard

---

### Post by ladybumavere on 2008-01-23
> **kinkyHelenMandarin said:**
> I'm not sure if anyone suggested it,
but ntfs support is not there by default,
u need to install ntfs-3g drivers (u'll find it in Synaptic):
[http://www.ntfs-3g.org/support.html](http://www.ntfs-3g.org/support.html)

Edit: no, sorry, I think there is ntfs support by default, but just for reading, anyway ntfs-3g works for me.


Thank you!

You pointed me in the direction I needed!

I went into the synaptic manager and downloaded ntfs-config and that, when run, will automatically detect NTFS drives and automatically configure them for you.

Worked perfect!

Thanks!

---

### Post by Vicfred on 2008-01-23
OMFG you read my mind i've come to post the same >_<

---

### Post by regomodo on 2008-01-23
do you dual boot windows? Linux won't boot ntfs partitions if they were improperly unmounted whilst in windows (read: a hard power off)

You can force it to mount, firstly just by going "sudo mount -av" which will retry to mount your fstab. It will then spit errors out and give you the actual command to enter to force it to mount. 

Once you've manage to do that delete the folder called "recycler". Can't remember the name exactly

---

### Post by Desperate on 2008-01-24
Sounded so nice, but I'm still stuck at the same line :(

ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount -av /dev/mapper/isw_bccebhcagd_RAID0 /media/windows
mount: you didn't specify a filesystem type for /dev/mapper/isw_bccebhcagd_RAID0
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
mount: /dev/mapper/isw_bccebhcagd_RAID0 already mounted or /media/windows busy
ubuntu@ubuntu:~$ 
Could that mean that my memory isn't sufficient for this trick I'm only working with one gig here??

Thanks anyway, small steps are bringing me forward too :), I'll get there in due time .

Richard

---

### Post by Desperate on 2008-01-24
Sounded so nice, but I'm still stuck at the same line :(

ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount -av /dev/mapper/isw_bccebhcagd_RAID0 /media/windows
mount: you didn't specify a filesystem type for /dev/mapper/isw_bccebhcagd_RAID0
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
mount: /dev/mapper/isw_bccebhcagd_RAID0 already mounted or /media/windows busy
ubuntu@ubuntu:~$ 
Could that mean that my memory isn't sufficient for this trick I'm only working with one gig here??

Thanks anyway, small steps are bringing me forward too :), I'll get there in due time .

Richard

---

### Post by SaeedTNT on 2008-01-24
I had same issue and solved that with installing a software I was downloaded from download.com about NTFS Fix

hope that help you

---

### Post by Desperate on 2008-01-24
Thank you! I'll give it a try this afternoon/night and report back here

Regards
Richard


EDIT:
Grand kids take lots of time though,didn't make it, but I'll be back  :)

Edit2 :
Couldn't find ntfs fix, but downloaded something that will let me read the disk , it's all there, but i can't touch it :) (or copy it to a saver place so I can make some real changes, but we'll get there in the end.

---

