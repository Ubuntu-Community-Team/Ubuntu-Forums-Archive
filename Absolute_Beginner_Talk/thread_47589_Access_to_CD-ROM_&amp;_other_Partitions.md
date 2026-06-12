---
title: "Access to CD-ROM &amp; other Partitions"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by jkarnacki on 2005-07-09
Hi.  I am using GRUB to dual boot ubuntu and windows 2000.  I have four partitions on my 80 gig hard drive: C, D, E, & F.  Ubunutu is installed on E, and Windows 2000 is installed on F.  I have no access to my other partitions or my cd-rom drive (G and H).

I have the little icon in my toolbar to mount stuff on drives.  one option says "open CD-rom drive", but it is un-clickable (greyed out).

Thanks.

<EDIT>
nevermind about the cd-rom drives, i figured that out.  but i still cant access my other partitions.  I can see my floppy drive, cd-rom and dvd-rom drives.  When i go to "my computer" i see all of those things.  i also see an icon called "filesystem", which appears to be my "E:\" partition which has ubuntu installed on it.
</EDIT>

---

### Post by mohaham on 2005-07-09
this might help you ...
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by jkarnacki on 2005-07-09
i guess im a super noob at ubuntu   :-P 

I opened up Terminal and typed

well actually i had no clue what i was typing.  but basically i am soooo confused i have no clue what to do with those commands.  i tried typing them in but they didnt do anything.

maybe some step by step instructions?  that would be erally nice of you.  If you need more information about my partition letters and folders just ask.  also, all i need is to be able to see my 3 other partitions which are C:\(windows 2000), D:\(nothing), and F:\(my files).  i want to be able to read and write to them.

---

### Post by mohaham on 2005-07-09
can u post the output of this command here...

sudo fdisk -l

---

### Post by jkarnacki on 2005-07-09
In Termnial, I type "sudo fdisk -l" and then type my password in and hit enter.  It gives me:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2         638     5116702+   5  Extended
/dev/hda2             639        1276     5124735    7  HPFS/NTFS
/dev/hda3   *        1277        1883     4875727+  83  Linux
/dev/hda4            1915        9729    62773987+   7  HPFS/NTFS
/dev/hda5               2         638     5116671    7  HPFS/NTFS
jeff@Ubuntu:~$
jeff@Ubuntu:~$
jeff@Ubuntu:~$
jeff@Ubuntu:~$


 :mad: 

Thanks.

---

### Post by mohaham on 2005-07-09
here's what u need to type to mount the Windows partitions..

sudo mkdir /media/C
sudo mount /dev/hda2 /media/C/ -t ntfs -o nls=utf8,umask=0222
sudo mkdir /media/D
sudo mount /dev/hda4 /media/D/ -t ntfs -o nls=utf8,umask=0222
sudo mkdir /media/F
sudo mount /dev/hda5 /media/F/ -t ntfs -o nls=utf8,umask=0222


to auto-mount them each time you boot in...

sudo gedit /etc/fstab

and append the below 3 lines to this file
/dev/hda2       /media/C    ntfs  ro,noatime,umask=0222      0       0
/dev/hda4       /media/D    ntfs  ro,noatime,umask=0222      0       0
/dev/hda5       /media/F     ntfs  ro,noatime,umask=0222      0       0

---

### Post by jkarnacki on 2005-07-09
wow are you great or what!!!  it worked like a charm.    I appreciate the help.  

---Jeff--- :)  \\:D/  \\:D/  :grin:  :grin:

---

