---
title: "sharing files between ubuntu and xp"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by buzzohall on 2007-05-31
is there any simple way that i can share my files between the two os's right now i have xp on c partition, d is a cd/dvd rw, e is a partition i call shared - this is the items i want to share, pictures, movies,  music, etc - and the ubuntu stuff after that.

also i have a dell xps wireless laptop and in the device manager in xp it says my network adapters anre 1294 net adapter-enabled, broadcom netxtreme 57xx gigabit controller- disabled, and Intel(R0 Pro/ Wireless 3945ABG Network Connection- enabled. how would i connect to the internet wirelessly? right now i have a dsl router that is encrypted. 

anything would help, even if it is pointing me to another thread, please help, much appreciated

---

### Post by rickycodie on 2007-05-31
get automatix, it has a ntfs mounter and you can use that to mount your partition and then read/write from it. 
just remove it before you upgrade or your upgrade will break

---

### Post by antoz on 2007-05-31
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 there is info in the above link about partitions and sharing

---

### Post by Smu on 2007-05-31
Automatix2 can automatically find and mount all your NTFS partitions, that is the easiest way to get to your XP files from ubuntu. The other way around there's a software called Ext2Fsd wich i use to mount my ubuntu filesystems in windows... 

Regarding the wireless, try to search the forum. You'll probably find someone else with the same problem, and hopefully a solution..

---

### Post by mlentink on 2007-05-31
I have an Intel Pro Wireless 3845 ABG on my Compaq nx7400, and it worked like a dream out of the box. Never had to do anything about it...

---

### Post by FerhatBingol on 2007-05-31
I also use under Windows, IFS drivers. It reads Linux partitions and mount them in Windows with any drive letter I want. 

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It is also a life saver sometimes...

[IMG]http://www.fs-driver.org/images/ScreenIfsDrives.gif[/IMG]

---

### Post by buzzohall on 2007-05-31
> **antoz said:**
> [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 there is info in the above link about partitions and sharing



i went to this site, and it is exactly how i have it set up- windows, a fat32, and the ubuntu stuff- and it says that ubuntu should mount and read my middle drive - e or shared- because it is a fat32, however when using ubuntu, it says it cannot mount the drive.

---

### Post by antoz on 2007-05-31
you most likely will have to open a terminal and mount it there, also edit your fstab so it mounts everytime you boot up. The link I gave has a page on mounting and below is an other good one, just copy and paste the commands that way you won't make any typo errors. In Ubuntu select what you want to copy and to paste clink the midddle wheel to paste.
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by mikemcfarlane on 2007-06-01
Hi buzzohall

I've been fighting with the same thing. During ubuntu install I didn't have a shared FAT 32 partition and wanted to add one afterwards to share data and which would mount during boot. The whole fstab and umask thing really got to me, but I'm there now.

Make sure you backup the /etc/fstab:
sudo cp /etc/fstab /etc/fstab_backup

To edit:
sudo gedit /etc/fstab

I had two ways for the drive to mount at boot that I added:
/dev/sda5 /media/sda5 vfat iocharset=utf8,umask=000 0 0

But I wasn't happy that everyone could read/write/execute files on this drive, so from:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
so my fstab is now:
/dev/sda5 /media/sda5 vfat utf8,user,auto,fmask=0177,dmask=0077,uid=1000 0 0
ie I am the only one who can read/write/execute.

I hope this helps.

Mike

PS My full fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d2116177-720c-4693-b7b0-c4537abee35e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2CE8541FE853E61C /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
# UUID=0210EC1110EC0D8B /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# 1.6.7 The following line mounts automatically, but is accessible by everyone.
#/dev/sda5 /media/sda5 vfat iocharset=utf8,umask=000 0 0
# 1.6.7 The following line mounts automatically and is only rwx by me.
/dev/sda5 /media/sda5 vfat utf8,user,auto,fmask=0177,dmask=0077,uid=1000 0 0
# /dev/sdb1
UUID=22746C3B746C13B7 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=c5f45bd9-1a50-4420-ba87-b19fbffe6901 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by BHelts on 2007-06-01
a good habit to get into is to use graphical sudo when starting up a GUI based program and requires elevation.

```
gksudo gedit /etc/fstab
```

heres a good [link]("http://www.psychocats.net/ubuntu/graphicalsudo") to help explain why.

---

### Post by mikemcfarlane on 2007-06-01
re. wireless

I can't find the websites I used, but try:
System>Administration>Network

You should see a wireless connection in there, in properties I set mine to roaming.

In the top right menu, click on the Networks icon and select your network. I think it should ask you for the key etc then. I have my router set to not broadcast, so this is causing a few probs, but notionally you should be clicking on the Network icon>Connect to other wireless networks and enter the SSID and key etc there.

Mike

---

### Post by Mazza558 on 2007-06-01
> **FerhatBingol said:**
> I also use under Windows, IFS drivers. It reads Linux partitions and mount them in Windows with any drive letter I want. 

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It is also a life saver sometimes...

[IMG]http://www.fs-driver.org/images/ScreenIfsDrives.gif[/IMG]

Yup. I have 130 GB Ext3 partition shared between Ubuntu and XP like this. Super fast and convenient!

---

### Post by buzzohall on 2007-06-07
alright here r the contents of my fstab file to show you i just started reading the reply and i am gonna post the contents, so if you see any errors let me know, this is before i have tied to edit the file.

---

### Post by antoz on 2007-06-08
You will have to add your Fat 32 partition to the fstab in the Terminal and then mount it 
/dev/**hdb1** /fat_files vfat iocharset=utf8,umask=000 0 0  (replace **hdb1** with yours) then mount it with
sudo mount -a
Have a really good look at the link below and follow the instructions. At the moment your Fat 32 partition is not in the Fstab

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

