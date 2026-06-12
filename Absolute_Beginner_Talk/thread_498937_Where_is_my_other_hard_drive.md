---
title: "Where is my other hard drive ?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by FreyaSmar on 2007-07-11
Emm.. Ok, I just installed Ubuntu.

The matter is, I have two hard Drives.
One of them I used to backup all my important documents.
The other one was the one where ubuntu should have been installed.

I cant find my backup hard drive :S

---

### Post by bodhi.zazen on 2007-07-12
> **FreyaSmar said:**
> Emm.. Ok, I just installed Ubuntu.

The matter is, I have two hard Drives.
One of them I used to backup all my important documents.
The other one was the one where ubuntu should have been installed.

I cant find my backup hard drive :S

I am going to move your question to Absolute beginner talk :)

Open a terminal

Enter the following command : ```
sudo fdisk -l
```

Post the output. More likely then not the data is there, just not mounted.

---

### Post by FreyaSmar on 2007-07-12
emmm and how do i mount it? 

:( i feel so stupid

---

### Post by ramjet_1953 on 2007-07-12
Try this:

1. Right-click on a blank section of your top, or bottom bar.

2. Select [COLOR="Blue"]Add to Panel[/COLOR]

3. Scroll down to [COLOR="Blue"]System and Hardware[/COLOR] and choose [COLOR="Blue"]Disk Mounter[/COLOR]

4. Click [COLOR="Blue"]Add[/COLOR]

5. Click[COLOR="Blue"] Close[/COLOR]

Any additional drives should now appear as icons on the bar.

Just click on the icon to mount it.

Regards,
Roger :cool:

---

### Post by FreyaSmar on 2007-07-12
I already tried that but it didnt work :S

---

### Post by Inxsible on 2007-07-12
Like bodhi said...post the output of ```
sudo fdisk -l
``` command -l is lowercase L

---

### Post by bodhi.zazen on 2007-07-12
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by FreyaSmar on 2007-07-12
It's not working :S and i feel somehow stupid everytime i tryy

---

### Post by bodhi.zazen on 2007-07-12
Well if you would like help beyond those links you will need to provide some information.

You can cut-and-paste fro the terminal. Highlight the text (in the terminal) -> move the mouse to firefox -> push the mouse wheel button down ;)

We need the output of ```
sudo fdisk -l
``` or at least the name of the partition you are trying to mount.

It will look like this :

```
sudo mkdir /media/doc
sudo mount /dev/hda1 /media/doc
```

could be /dev/sda1 rather then /dev/hda1

---

### Post by FreyaSmar on 2007-07-12
> freyasmar@freyasmar-desktop:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19742   158577583+  83  Linux
/dev/hda2           19743       19929     1502077+   5  Extended
/dev/hda5           19743       19929     1502046   82  Linux swap / Solaris

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   0  Empty
/dev/sda2              11        3648    29222235    b  W95 FAT32
Thats it..

---

### Post by bodhi.zazen on 2007-07-12
So you are trying to mount the FAT partition, /dev/sda2 ?

```
sudo mkdir /media/sda2
sudo mount -t vfat /dev/sda2 /media/sda2 -o umask=000
```

If you want it to mount at boot you will need to add an entry to /etc/fstab

/dev/sda2  /media/sda2  vfat  auto,users,umask=000  0  0

---

### Post by Inxsible on 2007-07-12
> **FreyaSmar said:**
> freyasmar@freyasmar-desktop:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19742   158577583+  83  Linux
/dev/hda2           19743       19929     1502077+   5  Extended
/dev/hda5           19743       19929     1502046   82  Linux swap / Solaris

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   0  Empty
/dev/sda2              11        3648    29222235    b  W95 FAT32

I am assuming that the 30 GB drive is the backup drive.
you can mount it as

```
sudo mount -t vfat /dev/sda1 /mnt/sda1 -o iocharset=utf8,umask=000
```

---

### Post by loomee on 2007-07-12
I need help please, I posted this question a while ago, but no seemed to answer

I installed ubuntu 7.04 and when I ran the installation I clicked on GNOME format then I got an error message so I decided to leave that section and proceed with installation. I was able to install ubunto which I am using right now to write this query.

 The problem is my windows OS is gone, I can not access it,all I see is disk1 in the desktop with an empty 73GB storage which is the size of my HD. My question is, did I really lose my windows OS and all my files? and is there away to restore or recover my OS and files?

I would appreciate any help.

---

### Post by bodhi.zazen on 2007-07-12
> **loomee said:**
> I need help please, I posted this question a while ago, but no seemed to answer

I installed ubuntu 7.04 and when I ran the installation I clicked on GNOME format then I got an error message so I decided to leave that section and proceed with installation. I was able to install ubunto which I am using right now to write this query.

 The problem is my windows OS is gone, I can not access it,all I see is disk1 in the desktop with an empty 73GB storage which is the size of my HD. My question is, did I really lose my windows OS and all my files? and is there away to restore or recover my OS and files?

I would appreciate any help.

Ummm .... 

Err ....

That sounds dire.

Can you post the output of ```
sudo fdisk -l
```

---

### Post by loomee on 2007-07-12
> **bodhi.zazen said:**
> Ummm .... 

Err ....

That sounds dire.

Can you post the output of ```
sudo fdisk -l
```

Hello bodhi,


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096    7  HPFS/NTFS
/dev/sda2            9328        9407      642600    5  Extended
/dev/sda3   *        9408        9729     2586465   83  Linux
/dev/sda5            9328        9384      457821   82  Linux swap / Solaris
/dev/sda6            9385        9407      184716   82  Linux swap / Solaris

Prior to installing Ubuntu, I had two drives on my HD, Drive C and D, and as you can see, they are both gone.

---

### Post by Inxsible on 2007-07-12
> **loomee said:**
> Hello bodhi,


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096    7  HPFS/NTFS
/dev/sda2            9328        9407      642600    5  Extended
/dev/sda3   *        9408        9729     2586465   83  Linux
/dev/sda5            9328        9384      457821   82  Linux swap / Solaris
/dev/sda6            9385        9407      184716   82  Linux swap / Solaris

Prior to installing Ubuntu, I had two drives on my HD, Drive C and D, and as you can see, they are both gone.

Dont worry...they are not gone. Linux doesnt assign drive letters. I can still see a NTFS drive which is called /dev/sda1. However thats the only one i see...so you might have erroneously erased one of the drives.

As a side note : you have two swap partitions which isnt very useful unless they are on two physically different drives or if they are located on different sectors of the drive. you could use GParted to reclaim that space back into one of the other partitions

---

### Post by bradmayne on 2007-07-12
try using the command:         df  -h

post the output.  I did a "how to" on viewing windows partitions a couple weeks ago.  That is basically the same thing as what we are doing now. (getting your other drive to mount)

---

### Post by loomee on 2007-07-12
Bodhi,

I can see the HD in my desktop but it's empty, no files. I downloaded Gparted, but I am so pre-newbie, so I dont  what to do next? By the way, I installed Ubuntu for the first time like 5 hours ago.

Hello Bradmayne,

This is what I got when I entered dh -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096    7  HPFS/NTFS
/dev/sda2            9328        9407      642600    5  Extended
/dev/sda3   *        9408        9729     2586465   83  Linux
/dev/sda5            9328        9384      457821   82  Linux swap / Solaris
/dev/sda6            9385        9407      184716   82  Linux swap / Solaris
loomee@loomee-laptop:~$ 
loomee@loomee-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             2.5G  2.0G  380M  84% /
varrun                633M  108K  633M   1% /var/run
varlock               633M     0  633M   0% /var/lock
procbususb            633M  112K  632M   1% /proc/bus/usb
udev                  633M  112K  632M   1% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   33M  600M   6% /lib/modules/2.6.20-15-generic/volatile
/dev/scd0             696M  696M     0 100% /media/cdrom0
/dev/sda1              72G   67M   72G   1% /media/disk
loomee@loomee-laptop:~$ 


Before the installation, I had as I mentioned 2 drive letters with roughly 25 GB free, now I think it's more than 70GB free

---

### Post by bodhi.zazen on 2007-07-12
> **loomee said:**
> Before the installation, I had as I mentioned 2 drive letters with roughly 25 GB free, now I think it's more than 70GB free

Well, it looks like you have had some data loss, hard to tell where and how it happened.

Linux uses different terminology for partitions, see this link :

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

OK, so you have with essentially 4 partitions.

/dev/sda1 1 9327 74919096 7 HPFS/NTFS  # this is your NTFS partition
/dev/sda2 9328 9407 642600 5 Extended 
/dev/sda3 * 9408 9729 2586465 83 Linux # I assume this is your Ubuntu root partition
/dev/sda5 9328 9384 457821 82 Linux swap / Solaris # First swap partition
/dev/sda6 9385 9407 184716 82 Linux swap / Solaris # Second swap partition

See Inxsible's post regarding two swap partitions. It does not hurt anything, but takes up disk space is all.


OK, your ntfs partition is mounted at /media/disk and yes it in fact looks empty.

/dev/sda1 72G **[color=red]67M**[/color] 72G 1% /media/disk

So I presume it was re-formatted some how :(

---

