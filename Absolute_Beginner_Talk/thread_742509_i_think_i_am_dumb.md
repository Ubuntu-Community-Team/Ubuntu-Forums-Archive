---
title: "i think i am dumb"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by the fish on 2008-04-01
i have 2 x 200gig external hd.  they mount but i can't see any files, they are formated ntfs. help please

---

### Post by Fixman on 2008-04-01
> **the fish said:**
> i have 2 x 200gig external hd.  they mount but i can't see any files, they are formated ntfs. help please

Have you mounted htem, by double clicking their icon on nautilus?

---

### Post by the fish on 2008-04-01
what is nautilus?

---

### Post by igknighted on 2008-04-01
the file manager (think windows explorer or konqueror or whatever OSX calls its file manager)

---

### Post by nachomania on 2008-04-01
I'm pretty sure you need for ntfs support...might not be an iossue any more. In the terminal, type in sudo nautilus (Im on a windows right now), and keep pressing the "up a directory" button (points up). See if you see anything there.

---

### Post by Fixman on 2008-04-01
> **the fish said:**
> what is nautilus?

You don't need to sudo. Just go to places->home folder, and double click the icons on the left side of the screen.

---

### Post by aomlives on 2008-04-01
If you are using Gnome, which comes with Ubuntu, then Nautilus is the file manager, like Explorer under Windows.

You can start it by opening up a terminal and typing nautilus. If you want to try to access the drives on your system, you could first try to look for them in the media directory on your filesystem. Normally they would also appear on your desktop.
If this is not the case, you can type directly in a terminal: "nautilus /media". Try to find your drives in the Nautilus window that opens.

greetz

---

### Post by the fish on 2008-04-01
the thing is they open but there are no files. they are both almost full and it says that they dont have anything on them.

---

### Post by Doorslammer on 2008-04-01
in terminal ```
fdisk -l 
``` post the output

you could also try ```
 sudo mount -a 
```


this will mount all drives  connected

one more ```
cat /etc/fstab
```
post the output ( lets see if there listed in there )

---

### Post by the fish on 2008-04-01
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06352ec8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b21caf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS

---

### Post by the fish on 2008-04-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=24bada32-d61e-49d4-aa20-28f4977b01cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e29fd15a-1665-4aa4-aa28-0aec1feee51a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Doorslammer on 2008-04-01
ok good /dev/sdb1 & also dev/sdc1 are your ntfs drives 
now you say there mounted 
if they are they should be in  /media/sdb1 & /media/sdc1 
cd to /media/ 
```
 ls 
```
should list 
something like this cdrom  cdrom0  data  floppy  floppy0  sdb1  sdc1

---

### Post by Doorslammer on 2008-04-01
if  they are mounted & you stil can't see them then you need the ntfs-config tool
make sure you have the ntfs-3g driver
```
sudo apt-get install ntfs-3g 
``` 

```
sudo apt-get install ntfs-config
```
use the ntfs-config tool to mount & make the drive read & write ;)

---

### Post by the fish on 2008-04-01
> **Doorslammer said:**
> ok good /dev/sdb1 & also dev/sdc1 are your ntfs drives 
now you say there mounted 
if they are they should be in  /media/sdb1 & /media/sdc1 
cd to /media/ 
```
 ls 
```
should list 
something like this cdrom  cdrom0  data  floppy  floppy0  sdb1  sdc1
Desktop    Examples                                Music     Public     Videos
Documents  libdvdcss2_1.2.9-2medibuntu4_amd64.deb  Pictures  Templates

---

### Post by the fish on 2008-04-01
still nothing

---

### Post by Doorslammer on 2008-04-01
lol ok  you just listed whats on your desktop or home folder most likely 
you did not read the part to cd /media/  then  ls
so ```
cd /media/
```
then ```
ls
```

---

### Post by Doorslammer on 2008-04-01
here  it's best if you follow this 
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
I know it's for feisty but it's still the same for gusty
post if you have any trouble after that

---

### Post by the fish on 2008-04-01
> **Doorslammer said:**
> lol ok  you just listed whats on your desktop
you did not read the part to cd /media/  then  ls
so ```
cd /media/
```
then ```
ls
```
cdrom  cdrom0  disk  disk-1


its been a long day

---

### Post by Doorslammer on 2008-04-01
ok  looks like your mount points are disk & disk-1 

if you do this should list your files 
```
cd /media/disk/ 
```
then ```
ls
```
ls stands for" list"
anyway I think if you
follow that guide   & post back if you have any trouble

---

### Post by Matthewslf on 2008-04-01
I am going to offer the usual solution for ntfs problems. In terminal type in
```
sudo apt-get install ntfs-3g
```
or hit Alt-F2 then:
```
gksudo apt-get install ntfs-3g
```
If it says it is already installed then don't worry about it. It might also help to say what type of connection they use (USB, FireWire, ...).

Edit: Chances are the guide above installs ntfs-3g anyway so don't bother with the above

---

### Post by Doorslammer on 2008-04-01
already offered that. he's new so  I'm trying to walk him through  it ;)
the drives are mounted he just can't see them , I was making sure they in fact mounted .  posted the ntfs-3g & the ntfs-config  plus posted a url for him to follow . he should get it now ;)

---

### Post by the fish on 2008-04-01
> **Doorslammer said:**
> ok  looks like your mount points are disk & disk-1 

if you do this should list your files 
```
cd /media/disk/ 
```
then ```
ls
```
ls stands for" list"
anyway I think if you
follow that guide   & post back if you have any trouble
i am going insane with this problem. still nothing is working

---

### Post by Doorslammer on 2008-04-01
hey follow the link I posted  if you really have files on there then you should be able to see/read them [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by the fish on 2008-04-01
> **Doorslammer said:**
> hey follow the link I posted  if you really have files on there then you should be able to see/read them [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
i did that.  nothing seems to work.

---

### Post by Doorslammer on 2008-04-01
are you daul boot with windows ?
boot in to windows & make sure there are files on there
 if you followed that guide & it still don't work  then I think your drives are empty I'v never seen it not work 
if the nffs format was messed up then you would get an error message but your not getting any error messages

---

### Post by the fish on 2008-04-01
i am not dualing booting but, i will try that. thanks for all the help.

---

### Post by Doorslammer on 2008-04-01
well  all I was saying is if you followed  that guide you should be able to see your files in your ntfs formated drives , we know there mounted 
try rebooting  after runing the ntfs-config tool 

also try to unmount them 
```
sudo umount /media/disk/
```
```
sudo umount /media/disk-1
```
then use the ntfs tool to mount them 

if all else fails 
try ```
 sudo mount /media/disk/  -o unhide 
```show all hidden and associated files/folders


if you don't have windows installed  & dual boot already  then don't do it now

---

