---
title: "[SOLVED] out of disk space"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-17
I have a dual boot system feisty with windows xp
I finally have my system to What i want but i am out of disk space i resized my windows partition with partition magic and with gparted now i just can't add it to my ubuntu partition. when i made it an ext3 it comes up lost and found and can't access it. when it is fat32 i can't save my podcasts to it or copy my docs to it and link to it. i would have just started with a new hard drive to begin with.

i am thinking of getting a new hard drive and swapping out the old one. 
how can i keep all of my hard work.

what files do i need to copy to the new install.

I am thinking of having a single ubuntu boot hard drive and just leave the other one as a spare for the rare time i need to go to my windows partition.

please help i don't want to start all my work again.
--------------------------------------------------------------------------------------------------
thanks folks, the best one i read was Microsoft gives you windows but Ubuntu gives you the whole house (home Folder) DarinB

---

### Post by HermanAB on 2007-08-17
The problem is thus:
The new partition is before the Ubuntu partition, so you cannot grow the Ubunto partition over it.  What you have to do instead, is format it (make a file system on it) then mount it somewhere where you can use it, say as /data.  Then you can save your overflow files on /data.

First, you need to figure out what the name of this partition is.  It will be listed in /dev and will not be listed with mount, since it is not mounted yet.  So do this:
$ mount
to get a list of existing mounted partitions in Ubuntu

then do:
$ ls /dev
to see what is there.  The partition will be listed as for example /dev/hda5 for example.  You need to figure out what is in /dev, that is not Windows and not in Ubuntu.

Now you have to prepare a file system:
$ sudo mkfs.ext3 -j /dev/hda5

Create a mount point in the Ubuntu partition:
# sudo mkdir /data

Mount the new file system:
# sudo mount -t ext3 /dev/hda5 /data

Now the new partition will be accessible as /data

So, it all comes down to figuring out what the name of the thing is and you don't want to format the wrong partition - that will be rather disappointing...

Cheers,

Herman

---

### Post by logos34 on 2007-08-17
sounds like it may be a permissions or ownership problem.  

Post the output for:
[B]
sudo fdisk -l[/B]

and
[B]
ls -l /media[/B]

---

### Post by Irony on 2007-08-17
Can't quite understand what you are saying but the following may be useful:

[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=13404.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=13404.0)

---

### Post by DarinB on 2007-08-17
darin@darin-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            2975        4778    14490630   83  Linux
/dev/sda3            4779        4863      682762+   f  W95 Ext'd (LBA)
/dev/sda4            1913        2974     8530515   83  Linux
/dev/sda5            4779        4863      682731   82  Linux swap / Solaris


Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9091    73023426    7  HPFS/NTFS
/dev/sdb2            9092        9729     5124735    b  W95 FAT32
darin@darin-desktop:~$ 

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9091    73023426    7  HPFS/NTFS
/dev/sdb2            9092        9729     5124735    b  W95 FAT32
darin@darin-desktop:~$ ls -l /media
total 32
lrwxrwxrwx  1 root  root    6 2007-08-08 15:24 cdrom -> cdrom0
drwxr-xr-x  2 root  root 4096 2007-08-08 15:24 cdrom0
drwxr-xr-x  2 root  root 4096 2007-08-08 15:24 cdrom1
dr-xr-xr-x  1 root  root 4096 2007-08-08 12:39 disk
drwx------ 32 darin root 4096 1969-12-31 19:00 disk-1
dr-xr-xr-x  1 root  root 8192 2007-08-09 12:30 disk-2
drwxr-xr-x  3 root  root 4096 2007-08-17 17:46 disk-3
lrwxrwxrwx  1 root  root    7 2007-08-08 15:24 floppy -> floppy0
drwxr-xr-x  2 root  root 4096 2007-08-08 15:24 floppy0
darin@darin-desktop:~$ 

/dev/sda1 ntfs my windows partition
/dev/sda4 the partition i just made comes up lost and found in nautilus UNUSABLE
/dev/sda2 my ubuntu partition
/dev/sda3 extended patition
/dev/sda5  linux swap 

so how do i use that ext3 as a part of ubuntu or do i have to reinstall the whole shebang and how do i save my stuff and transfer it?????

---

### Post by logos34 on 2007-08-17
looks like 'disk-3' is sda4.  (root owns it, hence the problem)

The easiest thing would be to make a permanent mount point and add an entry to fstab:

**sudo mkdir /media/sda4**  (*or '/media/data', '/media/storage', whatever, etc)
[B]
gksudo gedit /etc/fstab[/B]

add this line:
> 
/dev/sda4 /media/sda4 ext3 defaults 0 2

Reboot.

---

### Post by DarinB on 2007-08-17
it does mount automatically but still lost and found inaccessible


will the defaults stay the same. if i use this technique for my music hard drive that is ntfs????

this is not easy stuff for a beginner
thanks 
db

---

### Post by AlexenderReez on 2007-08-17
then mount it using script:)

---

### Post by logos34 on 2007-08-17
> **DarinB said:**
> it does mount automatically but still lost and found inaccessible


will the defaults stay the same. if i use this technique for my music hard drive that is ntfs????

this is not easy stuff for a beginner
thanks 
db

don't pay attention to the 'lost+found' folder--the system locks it.  Try to copy some files over to /media/sda4, not /media/sda4/lost+found.  Should be able to.

For ntfs partition, get ntfs-3g:

**sudo apt-get install ntfs-3g ntfs-config**

then,

**sudo ntfs-config**

--tick the box to enable write support 

It will automatically edit your fstab file so it mounts at boot

---

### Post by DarinB on 2007-08-17
this sounds good for my ntfs partition with my music but i am dealing with an ext3 partition that lies before my ubuntu partition and it comes up lost and found inaccessible

thanks i will try this for my windows partitions.
db

---

### Post by AlexenderReez on 2007-08-17
> **logos34 said:**
> don't pay attention to the 'lost+found' folder--the system locks it.  Try to copy some files over to /media/sda4, not /media/sda4/lost+found.  Should be able to.

For ntfs partition, get ntfs-3g:

**sudo apt-get install ntfs-3g ntfs-config**

then,

**sudo ntfs-config**

--tick the box to enable write support 

It will automatically edit your fstab file so it mounts at boot

for that,i  believe you need 

> deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

if your source list :)

and in terminal enter -->

> wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -

wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -

---

### Post by DarinB on 2007-08-17
Re my ntfs partition i have ntfs=3g and ntfs config and did enable read write i can read write bu tit won't mount at boot. this is another headache.


back to my ext3 problem with lost and found inaccessible.

thanks everybody
db

---

### Post by AlexenderReez on 2007-08-17
> **DarinB said:**
> Re my ntfs partition i have ntfs=3g and ntfs config and did enable read write i can read write bu tit won't mount at boot. this is another headache.


back to my ext3 problem with lost and found inaccessible.

thanks everybody
db

it is weird ...mine working hm..search ntfs synaptic...try to install all it dev ( for ntfs)...

---

