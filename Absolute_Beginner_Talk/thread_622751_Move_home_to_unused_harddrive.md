---
title: "Move /home to unused harddrive"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by martinja on 2007-11-25
Hi Guys,
I have looked at a lot of forums now to find out how I can make use of my secondary harddrive (has 35GB free space) but I don't feel confident about the names of drives and directories and files etc. I want to put my /home directory on it to take advantage of the greater space.
Firstly I don't know the name of the secondary harddrive. It is recognised by the operating system and is called LOCAL DISK on the desktop and in the /media directory. I think it is represented by in /dev as sdb5. When I do a mount in the Terminal this is the information I get:
[INDENT]martinjp@martinjp-server:~$ mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb5 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree) [LOCAL DISK]
/dev/sdb1 on /media/EXT DRIVE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree) [EXT DRIVE][/INDENT]

Secondly, I realise I have to mount it, move the /home directory into it then change /etc/fstab to let fstab know where the /home directory now lives.

Could someone **[SIZE="4"]please[/SIZE]** give me the steps I have to take to achieve this goal using the information I have given (or any information I can provide)????
Thanks in anticipation, I am now very unsure what I have to do.

---

### Post by Bothered on 2007-11-25
Could you post the results of:

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
ls -l /dev/disk/by-uuid
```

EDIT: Typo corrected
EDIT2: To explain these commands: The first lists the partition tables for all devices attached to the system, the second displays how partitions are mounted by default, and this third lists all system partitions by their UUID.

---

### Post by martinja on 2007-11-25
Thanks for the trouble, here goes:

> **Bothered said:**
> Could you post the results of:

```
sudo fdisk -l
```

[INDENT]Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfed5fed5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbcbcaaac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5356    43022038+   c  W95 FAT32 (LBA)
/dev/sdb2            5357        9964    37013760    f  W95 Ext'd (LBA)
/dev/sdb5            5357        9964    37013728+   b  W95 FAT32[/INDENT]


```
cat /etc/fstab
```

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=612c8ef9-8672-4ded-a3e9-ba6491ad0fd3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bcdc82c4-cf17-4fba-ba69-62c958a48fe5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0[/INDENT]


```
ls -l /dev/disk-by-uuid
```

martinjp@martinjp-server:~$ ls -l /dev/disk-by-uuid
ls: /dev/disk-by-uuid: No such file or directory
martinjp@martinjp-server:~$ ls -l /dev/bcdc82c4-cf17-4fba-ba69-62c958a48fe5
ls: /dev/bcdc82c4-cf17-4fba-ba69-62c958a48fe5: No such file or directory



---

### Post by mahiyar on 2007-11-25
This is a wonderful link complete in all respects to install a seperate home, I have used the same to do mine [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Partyboi2 on 2007-11-25
Here is a guide to changing /home to another partition
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Bothered on 2007-11-25
That last command should have been "ls -l /dev/disk/by-uuid" (slash, rather than - after disk), but that information isn't required at this stage.

Your system seems to have two hard drives, one small and one larger, but the larger one doesn't seem to have any free unformatted space. If you want to make use of the free space on this drive as a new /home partition, you'll need to:

1. Resize an existing partition to make room
2. Create a new partition
3. Copy files to the new partition (the files in /home)
4. Edit /etc/fstab to auto mount the new partition to /home on boot.

Instructions on how to do this can be given, but this is quite a complicated process and could result in data loss (at the partition resize stage).

---

### Post by martinja on 2007-11-25
> That last command should have been "ls -l /dev/disk/by-uuid" (slash, rather than - after disk), but that information isn't required at this stage.

[INDENT]martinjp@martinjp-server:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-11-25 14:30 2B1E-0DD6 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-11-25 14:30 2C47-1A04 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2007-11-25 14:30 612c8ef9-8672-4ded-a3e9-ba6491ad0fd3 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-25 14:30 bcdc82c4-cf17-4fba-ba69-62c958a48fe5 -> ../../sda5[/INDENT]

I have 2 CDROM drives, an External Harddrive (40GB of which most is used), 2 internal harddrives the boot drive has 9GB and the unused secondary drive (which is referred to as LOCAL DISK on the desktop) has 35GB and is virtually empty.. The latter is the one I want to put /home into.
Thanks for the consideration so far!

---

### Post by koenn on 2007-11-25
The disk you want to use, /dev/sdb if i'm not mistaking, has 2 partitions (actually 3: a primary partition, and an extended partition with a logical partition in it) and they're formatted with FAT32.
To use the entire disk as your new /home, you'll have to delete the existing partitions (you loose all data on it), create a new partition of type 83 (linux) spanning the entire disk, and format it, preferably with a linux native filesystem (eg ext3). 
This can be done with fdisk or by booting a GPartEd live cd. You'll have to watch out, eg don't delete partitions on /dev/hda, where your linux system now lives.

---

### Post by martinja on 2007-11-25
Thanks for the response so far, it has been frustrating but I am slowly starting to understand how things are done in Linux. BTW this info was really clear in explaining what each of the terms meant in the fstab file etc. [http://chris-linux.blogspot.com/2007/02/mounting-devices.html]("http://chris-linux.blogspot.com/2007/02/mounting-devices.html") 
I have just found something quiet inexplicable. When I disconnect my External Harddrive (only has 1 partition) then any reference to the secondary internal harddrive disappears. The following is **without** external harddrive physically connected:

[INDENT]martinjp@martinjp-server:~$ mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)[/INDENT]

This is the same query **with** external harddrive connected:

[INDENT]martinjp@martinjp-server:~$ mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb5 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree) [LOCAL DISK]
/dev/sdb1 on /media/EXT DRIVE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree) [EXT DRIVE]
[/INDENT]

Why should the fact that the external harddrive is connected or not means that the internal harddrive is detected???
How can I make sure that the internal harddrive stays connected (mounted??) so  can put my /home directory on it?

---

### Post by martinja on 2007-11-26
Could someone please explain this inconsistency??
Thanks!!

---

### Post by Partyboi2 on 2007-11-26
Not sure what your question is. Your external drive will be mounted as long as it is plugged in. If you are going to put your /home on the external hard drive it is going to have to be connected when ever you boot ubuntu. (from what I understand)
> /dev/sda1 on / type ext3 (rw,errors=remount-ro) []Is your internal hard drive and is mounted when you boot up ubuntu
>  /dev/sdb5 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma  sk=077,usefree) [LOCAL DISK]
/dev/sdb1 on /media/EXT DRIVE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma  sk=077,usefree) [EXT DRIVE]Is your external hard drive with 2 partitions on it, and are mounted at /media when your external hard drive is connected.

---

### Post by martinja on 2007-11-26
My External Harddrive  has only **one** partition on it. I confirmed this by plugging it into another computer with Win2000. The other drive referred to is (what I think is) an internal harddrive different from the one I boot off. The configuration of my computer when it was running Win2000, previous to installing Ubuntu, was C drive (9GB) and G drive 35 GB. After I installed Ubuntu it appeared to be only using the 9GB drive and not even identifying the 35GB drive unless the external harddrive was also connected. I'm confused.
If its any help I have a Compaq Deskpro EN P3 660MHz and 254RAM if anyone can identitfy the original setup of this computer.
Thanks

---

### Post by martinja on 2007-11-26
Thanks everyone for your fantastic assistance. I've worked out what my misunderstanding was ie. I was convinced that our external harddrive was only 40GB where infact it is 80GB and it was  patitioned into 2 sectors. Now I can go ahead with putting /home on the empty drive with better understanding.

---

### Post by koenn on 2007-11-26
> **martinja said:**
> Thanks everyone for your fantastic assistance. I've worked out what my misunderstanding was ie. I was convinced that our external harddrive was only 40GB where infact it is 80GB and it was  patitioned into 2 sectors. Now I can go ahead with putting /home on the empty drive with better understanding.
So it's that 80 GB external drive you'll put /home on ? If you're planning to use that drive on  Windows systems as well a on Linux systems; you might want to consider formatting it with  a Windows-compatible filesystem (FAT32) in stead of a linux-only filesystem such as ext3.

---

### Post by Partyboi2 on 2007-11-27
> **koenn said:**
> So it's that 80 GB external drive you'll put /home on ? If you're planning to use that drive on  Windows systems as well a on Linux systems; you might want to consider formatting it with  a Windows-compatible filesystem (FAT32) in stead of a linux-only filesystem such as ext3.
Can you put your /home on a windows filesystem? I know that linux can read windows file sytems but wasn't aware that you could move your /home to another file system.

---

### Post by koenn on 2007-11-28
> **Partyboi2 said:**
> Can you put your /home on a windows filesystem? I know that linux can read windows file sytems but wasn't aware that you could move your /home to another file system.
Both Windows and Linux can read FAT32. Reading NTFS from Linux works, writing usualy requires you install a NTFS filesystem driver - it works but i don't have first hand knowledge of how reliable it is. I also think I remember hearing about an ext3 driver for Windows, but that might be a myth. In any case, you can have a partition that can be read and written to from both Windows and Linux.

Now, if you'd attach that drive, with a linux user's home directory on it, to a computer running windows, it wouldn't magically change into a windows user profile, it would just be a directory containing files, e.g. gnome configuration files and .bashrc alongside whatever data you saved there. Now, if that data is in a format that windows applications can deal with (pdf files, mp3 files, open office tekst or spreadsheet files saved in MSOffice format, ....), you can use them from Windows as well. 


Disclaimer : this is all theory. Never tried it. myself.

---

### Post by maybeway36 on 2007-11-28
You can't put /home on FAT or NTFS without permission errors.

---

### Post by koenn on 2007-11-28
> **maybeway36 said:**
> You can't put /home on FAT or NTFS without permission errors.
I'm writing this from a computer with /home on an ext3 partition. I've been using it for 2 years now. No permission errors yet. I'll keep you posted.

---

### Post by koenn on 2007-11-28
> **maybeway36 said:**
> You can't put /home on FAT or NTFS without permission errors.
... but anyway, you got me wondering, so i quickly added a (virtual) harddrive to a (virtual) machine that alrady had a basic linux with fluxbox etc. Created a FAT32 (vfat) partition and filesystem on it, copied user home dirs to it, and told fstab to mount it to /home. I rebooted, and it seems to work. 

You were right in that you do have to pay attention to permissions here, I had to experiment a bit with mount options, chown and chmod, but basically, if you mount with rw,users, auto, check and if necessary change ownership of the dir with chmod (I copied as root so everything got owned by root, so i had to change that back), it appears to be working.
And of course, this was only a simple test with a fluxbox wm and some apps - maybe a gnome desktop is more demanding, but I'd say this is certainly possible.
Although personally, I'd fail more comfortable if my home was on a native linux fs.

---

