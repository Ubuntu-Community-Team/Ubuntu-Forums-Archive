---
title: "adding an  Extra harddrive in ubuntu"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by SLING on 2007-01-03
ok   so all i have to do is add this hard drive , it wont let me , 

can  anyone  give me a complete list of all the directions i  need to do it?

---

### Post by taurus on 2007-01-03
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Efwis on 2007-01-03
we can help you, but we need a little more info

is this HDD for storage or does it have another OS on it?
is it formatted and what type of format ntsf or fat32.

what have you done so far to add it into your Ubuntu system?

---

### Post by Bachstelze on 2007-01-03
First, make sure you drive is correcly detected in your BIOS and in Ubuntu (*sudo fdisk -l*). Then, for each partition you want access to, you must create a *mountpoint*, which is the directory on your filesystem where the files on the partition will go. Usually, they're created in /mnt or in /media so for example, if your partiiton contains your music, you can do :

```
sudo mkdir /media/MyMusic
```

then you mus mount your partition, which is the hardest part. Paste the output of *sudo fdisk -l* and we'll tell you how to do it.

---

### Post by SLING on 2007-01-03
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by SLING on 2007-01-03
i tried mounting it before and i  had it going  but i could not change the permissions,  so i  started over.

---

### Post by taurus on 2007-01-03
```
**sudo fdisk -l** <-- that is letter l as in larry...
```

---

### Post by SLING on 2007-01-03
it does not have an os on it, i  want it soely for storage,  what  drive  type do i  want to select for it  when i  set it up in the disc menu ?

---

### Post by taurus on 2007-01-03
But I need to know the device, /dev/hdb1 or whatever, and the filesystem before I can show you how to mount it!!!

---

### Post by Efwis on 2007-01-03
is this a SATA drive or IDE drive?

also you said you had it going once before, can you redo your steps you did to make it work?

---

### Post by SLING on 2007-01-03
sudo fdisk -l <-- that is letter l as in larry...


that doesnt work
 
just  typing in  sudo fdisk works 

am i typing it wrong?

---

### Post by taurus on 2007-01-03
You only type in this part in a terminal!

```
**sudo fdisk -l**
```

---

### Post by SLING on 2007-01-03
Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         981     7879851   83  Linux
/dev/hda2             982        1027      369495    5  Extended
/dev/hda5             982        1027      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        1027     8241345    f  W95 Ext'd (LBA)
/dev/hdb5               2        1027     8241313+   b  W95 FAT32

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7294    58589023+   c  W95 FAT32 (LBA)

---

### Post by SLING on 2007-01-03
ya  i  did type it in the terminal,  i  guess i must have gotten my spacing wrong 

anyway , that s what popped up .

---

### Post by taurus on 2007-01-03
And I assume you want to mount /dev/sda1...  Edit /etc/fstab from a terminal with

```
gksudo gedit /etc/fstab
```
Scroll down to the bottom and add this line.

```
/dev/sda1   /media/sda1   vfat    iocharset=utf8,umask=000   0   0
```
Save it.  Then, create a new mount point and mount it...

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

### Post by SLING on 2007-01-03
i cannot  remeber how i made it work last time , and i dont really feel like spending five hours typing  in the terminal, does anyone have a faster way ?

---

### Post by taurus on 2007-01-03
Have you tried my method from above???  It takes like less than a minute and with cut 'n paste, it takes less than 30 seconds...  ](*,)

---

### Post by SLING on 2007-01-03
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             7.4G  1.9G  5.2G  27% /
varrun                 94M   84K   94M   1% /var/run
varlock                94M  4.0K   94M   1% /var/lock
udev                   94M  112K   94M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   19M   76M  20% /lib/modules/2.6.15-23-386/volatile
/dev/sda1              56G   17G   40G  30% /media/CORE
/dev/sda1              56G   17G   40G  30% /media/sda1

---

### Post by SLING on 2007-01-03
i think i  mounted my exturnal hardrive by accident

---

### Post by taurus on 2007-01-03
You might want to unmount the first one then!!!

```
sudo umount /media/CORE
```

---

### Post by SLING on 2007-01-03
i h ave my drive mounted now  but  i cant change my permissions

---

### Post by taurus on 2007-01-03
You don't need to change any permission since you should be able to write to /media/sda1 with the **umask=000** in /etc/fstab...

---

### Post by SLING on 2007-01-03
SD1 is just  a blank on the disc menu , i  wanted to  mount a drive called hdb5

---

### Post by SLING on 2007-01-03
anyway  i just  unmounted it ,because i couldnt  acess hdb5  , im  gonna remove the drive , start  up ,  check it then  put it back in after shut down ,  should i  enable the drive under discs first  before mounting it  in the terminal?

---

### Post by taurus on 2007-01-04
Just add this line to /etc/fstab...

```
/dev/hdb5   /media/hdb5   vfat    iocharset=utf8,umask=000   0   0
```
Then, create a new mount point for it.

```
sudo mkdir /media/hdb5
sudo mount -a
df -h
```

---

### Post by SLING on 2007-01-04
t I need to know the device, /dev/hdb1 or whatever, and the filesystem before I can show you how to mount it!!!


 what did you mean by filesystem? Im  sorry i gues i  missed this post

---

### Post by SLING on 2007-01-04
ok

 ill   try that

---

### Post by SLING on 2007-01-04
i f i mount  it , how will i  know it works, and what if,  if i still cant access the drive?

---

### Post by taurus on 2007-01-04
The "**df -h**" command will tell you whether the partition is mounted (and to where) or not!!!  And try to copy something to it with nautilus to see if you can write to it...

---

### Post by SLING on 2007-01-04
i get  this when i  try to  acess it 

 

only root can mount /dev/hdb5 on /media/hdb5

---

### Post by taurus on 2007-01-04
```
sudo mount -a
df -h
```

---

### Post by SLING on 2007-01-04
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by SLING on 2007-01-04
thats what i  get  when i  type what  you listed

---

### Post by taurus on 2007-01-04
Let's have a look at your /etc/fstab again!!!  Paste the output here...

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by SLING on 2007-01-04
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdb5   /media/hdb5   vfat    iocharset=utf8,umask=000   0   0

---

### Post by SLING on 2007-01-04
:-k :-k :-k

---

### Post by SLING on 2007-01-04
could  i just unmount the drive , remove the folder locations,and start over ?

---

### Post by SLING on 2007-01-04
if its any help at  all,  I'm  using dapper drake

---

### Post by SLING on 2007-01-04
im gonna  log off for now , I'll check  ack  later for a reply , thanks for your help

---

### Post by SLING on 2007-01-09
SO  CAN  ANYONE HELP ME  from  my last post  ?

---

### Post by SLING on 2007-01-09
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

/dev/hdb5 /media/hdb5 vfat iocharset=utf8,umask=000 0 0

---

### Post by SLING on 2007-01-11
i think if i change the mount location and overwrite the old one itll  work ,  any  sugesstions??

---

### Post by SJN2k on 2008-03-26
I wasn't sure whether to start a new thread or just add to this one, but here goes.

I have Ubunto 6 LTS running on a Dell Poweredge server which I am trying to convert into a mail server running Zimbra.

I have downloaded and started the install only for it to tell me that I have insufficient disc space. I have a single 8G SCSI hard drive at the moment.

The server has 5 more free SCSI hotswap bays and I have another 8 G drive pulled from a windows 2000 server (I don't know what's on the drive in terms of files etc but it can all be got rid of).

What I need to be able to do is to add this drive on to the server so that I can use it to install the Zimbra ZCS on it. 
I am a complete newbie to a) Linux, b) Ubuntu and c) Zimbra  so I would appreciate someone pointing me in the right direction with regard to getting this drive up and running.

Many thanks

---

