---
title: "2nd HD permission help"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2006-07-20
I jumped headlong into Ubuntu today after XP tried to get me to install the Orwellian Windows Genuine Advantage crap again.  First linux distro ever...

I kept my XP partition on my first HD, along with the new Ubuntu install and I moved all the stuff I really wanted to keep to my 2nd, larger HD (120GB)  Now I cant access any of it.  I tried changing the file permission from the Nautilus program but I can not see anything even on the first level.  All my writing, MP3, "personal" videos... everything important is there...

I really hate booting up the slow XP after I have seen how fast Ubuntu comes up... any pointers on how to open it up?

Something about a terminal?

I am computer literate in a windows way... this is all foriegn to me so far

---

### Post by catlett on 2006-07-20
The terminal is where you enter commands. It is found under Applications<Accessories<Terminal

Is there an icon for it on your desktop?
Does it say you do not have permissin to view it or something like that?

Open up the terminal and put these commands in. Then post the output
```
sudo fdisk -l
```
```
cat /etc/fstab
```
The first one will list your partitions. The second one is a view of the file that tells the computer which partitions to mount on start up.

---

### Post by hanzomon4 on 2006-07-20
What file system do you have on the hard drive in question... ntfs, fat32(vfat),...?

---

### Post by Cornbreadly on 2006-07-20
The results of the fdisk:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        5189    41640480    7  HPFS/NTFS
/dev/hda3            5190        7207    16209585   83  Linux
/dev/hda4            7208        7297      722925    5  Extended
/dev/hda5            7208        7297      722893+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241    7  HPFS/NTFS

fstab results

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Is that five partitions for my little 60 GB HD?

---

### Post by catlett on 2006-07-21
Sorry for the long reply. Yes you have 5 partitions. But in reality you have 4. An extended partition holds logical partitions so it doesn't take up any space of it's own, it shares the space.

You have 4 partitions that can be mounted from your first hard drive and 1 from your second drive but you only have 2 beong mounted. (hda3 and hda5)

You need to add entries for the other partitions so they can be mounted and you can access them. 
First we have to make a place for them to be mounted to. Open the terminal and enter this
```
sudo mkdir /media/windows
```
```
sudo mkdir /media/backup
``` Now we are going to make a backup of your /etc/fstab file just to be safe ```
sudo cp /etc/fstab /etc/fstab_backup
```If something goes wrong, you can switch back to your old list with ```
sudo cp /etc/fstab_backup /etc/fstab
```
Now we have to edit the /etc/fstab file. Enter this command to open the document in a text editor.
```
sudo gedit /etc/fstab
```
add thes two lines to the list. (it doesn't matter where. It doesn't have to be in any order, just put them on the next line available)
```
/dev/hda2       /media/windows    ntfs    defaults,nls=utf8,umask=007,gid=46  0   1
```
```
/dev/hdb1             /media/backup     ntfs   defaults,nls=utf8,umask=007,gid=46  0   1 
```

so your document should look like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc       /proc             proc  defaults    0 0
/dev/hda3  /                 ext3  defaults,errors=remount-ro 0 1
/dev/hda5  none              swap  sw      0 0
/dev/hdd   /media/cdrom0     udf,iso9660 user,noauto 0 0
/dev/hda2  /media/windows    ntfs  defaults,nls=utf8,umask=007,gid=46  0   1
/dev/hdb1  /media/backup     ntfs  defaults,nls=utf8,umask=007,gid=46  0 1
```The partitions will mount on your next start up. NTFS has only read capability in linux. You can view a document, photo or play a movie, mp3 but you can't write or delete to it.There are some apps that can do it but they are reversed engineered and can possibly cause corruption in the partition.
This is a driver that will let you access your ubuntu partitiuon from windows, with read and write abilities. [http://www.fs-driver.org/](http://www.fs-driver.org/)

These are the only partitions with data you want . hda1 is Dell's recovery partition. hda4 is the extended partition that isn't a stand alone partition, it holds hda5.
hda5 is the swap partitiuon which is virtual memory space (likw windows swap file, if your ram runs out the system can use hard drive space as additional ram)
Here are a couple of links to explain /etc/fstab better [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

