---
title: "[SOLVED] missing hard drive"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Doorslammer on 2008-02-08
I'm missing a vfat 80 gig 
new to linux   so  not sure how to go about it
gusty 7.10 
the drive is internal I can see one of the 80 gig's primary but can't see the secondary 80 
hey guy's I have a good question
I'm missing one of my 80gig drives . it does not show up in / media
```

so i did fdisk -l

Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4faaccd1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bb290cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9732    78172258+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0478ffb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   c  W95 FAT32 (LBA)

```
now I have no idea what all that means    it seems to be listing both 80 gig's but how do I mount it? 
I can't see the secondary 80 gig 
again only one is listed in my media

---

### Post by emarkd on 2008-02-08
Run

```
mount
```

and it'll tell you where everything's mounted

---

### Post by jan quark on 2008-02-08
run 

```
ls /media
```
and post the output to see which drive is missing and which one hast to be mounted 

to mount try this
make a new mount point with

```
sudo mkdir /media/data
```

and then mount the drive with 

```
sudo mount /dev/sda1 or sdb1 /media/data -t vfat -o umask=000
```

---

### Post by Doorslammer on 2008-02-08
doorslammer@ubuntuslammer:~$ ls /media
cdrom  cdrom0  floppy  floppy0
doorslammer@ubuntuslammer:~$

---

### Post by jan quark on 2008-02-08
well I was a little too overhasty

run ```
mount
``` 
as suggested emarkd

you can also look in the mnt folder
```

ls /mnt
```
to look for your missing drive

---

### Post by Doorslammer on 2008-02-08
doorslammer@ubuntuslammer:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev                       )
/dev/sdb1 on /media/data type vfat (rw,umask=000)
/dev/sda1 on /media/data type vfat (rw,umask=000)
doorslammer@ubuntuslammer:~$

---

### Post by Doorslammer on 2008-02-08
sda1 is showing  & is mounted (has always shown up)
sdb is the one missing

---

### Post by jan quark on 2008-02-08
try this

run

```
gksudo gconf-editor
```

go to apps > nautilus > desktop and check the boxes for the missing drives

just a wild guess

---

### Post by emarkd on 2008-02-08
Can you post the output of 

```
cat /etc/fstab
```

It looks like they're trying to mount to the same location...

---

### Post by jan quark on 2008-02-08
hm 
perhaps creating another mount point and mounting it there would solve this

---

### Post by Doorslammer on 2008-02-08
```
doorslammer@ubuntuslammer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=ee8a9387-5e1b-4396-919c-fe9f909ecfff /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=121ab551-a594-4625-a195-a6659f721f5f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
doorslammer@ubuntuslammer:~$ 
```

---

### Post by emarkd on 2008-02-08
> **jan quark said:**
> hm 
perhaps creating another mount point and mounting it there would solve this

I'm sure you're right, but when he reboots fstab is going to mess it up again.  That's why we need to see that fstab file ;)

---

### Post by emarkd on 2008-02-08
Guess I'm wrong about that.. :)

So lets unmount /dev/sdb1

```
sudo umount /dev/sdb1
```

Then make a mount point:

```
sudo mkdir /media/b
```

Then mount it there:

```
sudo mount /dev/sdb1 /media/b -t vfat -o iocharset=utf8,umask=000
```

That's assuming it's a FAT32 drive, which I think you said it was....

---

### Post by Doorslammer on 2008-02-08
ok just did that 
still does not show up in media 
or should I be looking else where ?

---

### Post by jan quark on 2008-02-08
well I se only the linux main partition, swap partition, floppy and cdrom

I would suggest
the following

make a backup of this fstab file

```
sudo cp /etc/fstab /etc/fstab_backup
```

then run this
```

ls /dev/disk/by-uuid/ -alh
```

we now see the UUID numbers for the filesystem

now run 

```
sudo parted /dev/sda p
```




to see exactly which  partition is which


make a new mount point in media as posted aove

```
sudo mkdir /media/newdata
```


now run
```

gksudo gedit /etc/fstab
```


and add this 

```
/dev/sdb1     
UUID=285F98566380864A   /media/newdata   vfat iocharset=utf8,umask=000     0       2
```

changing the uuid in accordance with your uuid 


man I hoe there is a shorter solution

but that are mine 2 cents

---

### Post by emarkd on 2008-02-08
If everything work ok there, your drive is mounted at /media/b and you can view your files in there.  Of course, you could've changed that to whatever you wanted to call it...

---

### Post by jan quark on 2008-02-08
cool emarkd :)
are we both wrong :confused:

---

### Post by Doorslammer on 2008-02-08
ok whent to sytem/media/b & it said error no midia

---

### Post by emarkd on 2008-02-08
what do you get now if you run

```
mount
```

---

### Post by Doorslammer on 2008-02-08
ok I have not run the last post with  yet 
sudo cp /etc/fstab /etc/fstab_backup

seems confusing to me
what the heck is my un number ? 1000 ?  only user

---

### Post by Doorslammer on 2008-02-08
doorslammer@ubuntuslammer:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/data type vfat (rw,umask=000)
/dev/sda1 on /media/data type vfat (rw,umask=000)
/dev/sdb1 on /media/b type vfat (rw,iocharset=utf8,umask=000)
doorslammer@ubuntuslammer:~$

---

### Post by hyper_ch on 2008-02-08
using the  tags [ code ] [ / code ] makes such stuff much easier to read.

---

### Post by bodhi.zazen on 2008-02-08
> **hyper_ch said:**
> using the  tags [ code ] [ / code ] makes such stuff much easier to read.

he he he ... and use noparse to show them ;)

[noparse][noparse]```

```[/noparse][/noparse]

yields

[noparse]```

```[/noparse]

Aslo use noparse to disable smiles in blocks of text / code

---

### Post by Doorslammer on 2008-02-08
```
doorslammer@ubuntuslammer:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/data type vfat (rw,umask=000)
/dev/sda1 on /media/data type vfat (rw,umask=000)
/dev/sdb1 on /media/b type vfat (rw,iocharset=utf8,umask=000)

```
funny it's not loading  or mounting the sdb1.
in windows it's always worked  it's a fat32 just like sda1
yet no matter what we do it's not doing it

---

### Post by bodhi.zazen on 2008-02-08
The "problem" is each partition needs a unique mount point :

> [b]/dev/sdb1 on /media/data type vfat (rw,umask=000)
/dev/sda1 on /media/data type vfat (rw,umask=000)[/b]
/dev/sdb1 on /media/b type vfat (rw,iocharset=utf8,umask=000)

Post the contents of your current /etc/fstab and the output of ```
ls /media
```

---

### Post by Doorslammer on 2008-02-08
```
 ls /media
b  cdrom  cdrom0  data  floppy  floppy0
doorslammer@ubuntuslammer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=ee8a9387-5e1b-4396-919c-fe9f909ecfff /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=121ab551-a594-4625-a195-a6659f721f5f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by Doorslammer on 2008-02-08
```
doorslammer@ubuntuslammer:~$ fdisk -l

Disk /dev/hda: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6adf6ad

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2494    20033023+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4faaccd1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bb290cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9732    78172258+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0478ffb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   c  W95 FAT32 (LBA)
doorslammer@ubuntuslammer:~$   

```

---

### Post by Doorslammer on 2008-02-08
could it be sda1 & sdb1 have the same id c ? if you look at the fdisk -l stats I just posted

---

### Post by bodhi.zazen on 2008-02-08
kk, lets do some housekeeping :)

```
sudo umount /dev/sdb1
sudo umount /dev/sda1
```

now , re-run the mount command to make sure those partitions are no longer mounted.

OK, lest give each partition a unique mount point:

```
sudo rm -rf /media/data /media/d
sudo mkdir /media/sdb1 /media/sda1
```

DO NOT RUN THAT rm -rf COMMAND IF YOUR PARTITION IS STILL MOUNTED (it will erase the data on the partition if you do)

You can give each whatever name you wish, as long as they are unique (ie /media/data1 /media/data2, whatever)

OK, now lets edit /etc/fstab :

```
gksu gedit /etc/fstab
```

Add these lines :

```
# Added drives

/dev/sda1 /media/sda1 vfat auto,user,uid=1000,gid=100,umask=007 0 0
/dev/sdb1 /media/sdb1 vfat auto,user,uid=1000,gid=100,umask=007 0 0
```

Now mount 'em

```
mount -a
```

and list 'em

```
ls /media/sda1
ls /media/sdb1
```

See this link for further info :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Doorslammer on 2008-02-08
damn it still nothing on sdb1  no go 
no matter what you had me do it don't work  for the missing drive 
sda1 mounts with np like always  ever since I installed ubuntu 7.10 is has worked but never had sdb1

if fdisk can see it  why would I not be able to mount it

---

### Post by jan quark on 2008-02-08
Doorslammer I officialy dub your thread the trickiest of all my threads ever so far... :)
I will keep an eye on this thread but right now I have no ingenious idea

---

### Post by hyper_ch on 2008-02-08
> **bodhi.zazen said:**
> he he he ... and use noparse to show them ;)

I forgot what they were called... [noparse][nocode][/nocode][/noparse] was wrong... but didn't remember that actual ones. Also in the tinymce editor (I think it is) the noparse tags aren't listed.

---

### Post by Doorslammer on 2008-02-08
hey I rebooted (power outage for about 5minutes) & now I can see it  but it's still not listed in my media 
/media/sdb1/
how do I link it to my storage media

---

### Post by jan quark on 2008-02-08
where do you see it?

you mean the missing drive is found eventually?

---

### Post by Doorslammer on 2008-02-08
/media/sdb1/  yes the missing drive now works it's mounted  it mounted at boot

if I go to my storage media & type in /media/sdb1/
I go right in to the drive & see the files. I can access them too.
but if I just go to storage media I can't see the drive there is no drive icon for sdb1

---

### Post by jan quark on 2008-02-08
good to hear you can access your files on the "ghost drive"

please run once again these commands, i know it is a little repetitive

```
mount
```
```

sudo fdisk -l
```
```

ls /media
```

and try to press ctrl + H in the media to show hidden files wild guess

---

### Post by Doorslammer on 2008-02-08
```
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,noexec,nosuid,nodev,uid=1000,gid=100,umas                   k=007)
/dev/sdb1 on /media/sdb1 type vfat (rw,noexec,nosuid,nodev,uid=1000,gid=100,umas                   k=007)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev                   )
doorslammer@ubuntuslammer:~$ sudo fdisk -l
[sudo] password for doorslammer:

Disk /dev/hda: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6adf6ad

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2494    20033023+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4faaccd1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bb290cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9732    78172258+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0478ffb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   c  W95 FAT32 (LBA)
doorslammer@ubuntuslammer:~$ ls /media
b  cdrom  cdrom0  data  floppy  floppy0  sda1  sdb1
doorslammer@ubuntuslammer:~$ 
```

---

### Post by Doorslammer on 2008-02-08
first image is storage media
[http://www.digitalboneyard.com/forum3/files/4988.jpg](http://www.digitalboneyard.com/forum3/files/4988.jpg)
this one is media/sdb1
[http://www.digitalboneyard.com/forum3/files/4989.jpg](http://www.digitalboneyard.com/forum3/files/4989.jpg)

---

### Post by jan quark on 2008-02-08
you know what that is weird 
it seem everything is correct, you can access the files and the drive is mounted

one small step is missing and IMHO it must be something with the display settings or in the display preferences, some option which enables the display of all mounted drives

but honestly I do not know the kde desktop well, close to nothing is my knowledge in this field

---

### Post by Doorslammer on 2008-02-08
well then Thank you very much for all the help .
I can at lease access the drive & know where to find it 

so problem solved  in my book 
Thanks again you have been much help :D

---

### Post by jan quark on 2008-02-08
glad to hear
one thing more, perhaps post a last time here after you have done few reboots, to check if the drive is really properly mounted or if we had just luck with this one reboot :)

but you dont have to restart now several times :)

when everything works well please mark this thread as solved using the thread tools

and feel free to ask whatever you want to know

thank you

---

### Post by bodhi.zazen on 2008-02-08
> **hyper_ch said:**
> I forgot what they were called... [noparse][nocode][/nocode][/noparse] was wrong... but didn't remember that actual ones. Also in the tinymce editor (I think it is) the noparse tags aren't listed.

Yea, we hid the code here :

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by hyper_ch on 2008-02-08
couldn't it be integrated into TinyMCE?

---

