---
title: "Mounting slave drive with permissions"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by likwid on 2005-10-16
Hi

I'm trying to mount a slave media drive (ext3) in the home folder of my user account. This works ok using System-admin-disks tool, but i do not have permission to view or manipulate the mounted files or folders. 

Please help, this transition is not as smooth as i could have wished and my sunday is disappearing as my frustration increases.

---

### Post by SilentCacophony on 2005-10-16
Hi. Usually, in Ubuntu, you should mount drives in the /media folder. If you already have it mounted somewhere else, it would probably help if you posted the output of these commands in a terminal:

sudo fdisk -l

df -h

cat /etc/fstab

Also, are you looking for a temporary mount or a permanent one?

---

### Post by likwid on 2005-10-16
Hi. Thanks so much for your reply.

In reponse to command sudo fdisk-l
> 
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+  83  Linux
/dev/hda2            2433       24321   175823392+   5  Extended
/dev/hda5           23944       24321     3036253+  82  Linux swap / Solaris
/dev/hda6            2433       23943   172787044+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24320   195350368+   7  HPFS/NTFS

df -h
> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              19G  1.9G   16G  11% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hda6             163G  148M  154G   1% /home
df: `/media/cdrom0': No such file or directory
/dev/hdb1             184G  165G  9.8G  95% /home/mark/Desktop/Media
/dev/hdb1             184G  165G  9.8G  95% /media


cat /etc/fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Having mounted in media i find that i do not have permissions to access folders, they are accessible as root.

I'm looking to create a permanent mount. 

Thanks !

---

### Post by SilentCacophony on 2005-10-16
Ok, I see a couple of potential problems there:

*/dev/hdb1 184G 165G 9.8G 95% /media*

Mounting directly to /media seems like a really bad idea, though I've never tried it. I'm not sure what potenetial problems that may cause. Something like /media/Media would be more appropriate.

*/dev/hdb1 * 1 24320 195350368+ 7 HPFS/NTFS*

Your fdisk -l shows the slave drive as NTFS, not ext3. Do you know if that's correct? Write support for NTFS from within linux is pretty much unsupported. I hear that it can be done, but that it's dangerous.

There is a guide to mount NTFS as read only [here]("http://www.ubuntuguide.org/#automountntfs") that explains the process, where you would want to change /dev/hda1 to /dev/hdb1, because you're using the second drive.

EDIT - I forgot to add that if you have room to copy whatever files you have on the NTFS drive to your linux, or another drive, it would be better to use FAT32 as the filesystem on the media drive, as both windows and linux can read and write to that.

---

### Post by likwid on 2005-10-16
It /shouldn't/ be NTFS. Certainly, in the disk manager tool it is reported as Ext3. 

Some background. I have two 200 gig disks which previously held windows and a lot of media. I managed to copy most the media onto one ntfs drive(1) and backed up what was left on dvd.

Having installed ubuntu on an old 6 gig drive, i was able to format the other ntfs drive(2) ext3 then copy the media onto it. Then i was able to partition, format and install ubuntu on drive(1). At this stage i thought ntfs was gone completely.

I very much appreciate your help.

---

### Post by SilentCacophony on 2005-10-16
Well, If you've copied off the media, it may be worth trying something like gparted from a live cd, or by installing it in ubuntu, to examine that drive and maybe format it as FAT32, or ext3 if it's not. I don't have any experience with NTFS myself, but I do know that if you mount an ext3 drive from /etc/fstab with 'defaults' as the options, it'll be read/write by default.

Also, while the drive is mounted to /media, it may be confusing to ubuntu if you try mounting again *within* /media, so you may want to try to unmount that:

**sudo umount -l /media**

and verify that it's not listed under **df -h** output after that.

If you do want to try it as ext3, the procedure is similar to what that guide shows, but you'd add a line like so to /etc/fstab:

```
/dev/hdb1       /media/Media     ext3    defaults        0       2
```

and then mount it with **sudo mount -a**

---

### Post by likwid on 2005-10-16
Thanks again.

I'm able to mount the drive but still i do not have permission as normal user to even view them.

---

### Post by SilentCacophony on 2005-10-16
> I'm able to mount the drive but still i do not have permission as normal user to even view them.

That's not normal. By default, you should be able to read from the drive as any user. If you mounted the drive to a folder within /media, you should be able to see the permissions of the various mount points by performing **ls -l /media** in a terminal.

For example, mine looks like so:

```
brian@ubuntu:~$ ls -l /media
total 36
lrwxrwxrwx   1 root  root     6 2005-10-14 13:36 cdrom -> cdrom0
drwxr-xr-x   2 root  root  4096 2005-10-14 13:36 cdrom0
drwxr-xr-x   2 root  root  4096 2005-10-14 13:36 cdrom1
lrwxrwxrwx   1 root  root     7 2005-10-14 13:36 floppy -> floppy0
drwxr-xr-x   2 root  root  4096 2005-10-14 13:36 floppy0
drwxr-xr-x   7 root  root  4096 1969-12-31 19:00 hda1
drwxr-xr-x  22 root  root  4096 2005-10-13 14:10 hda2
drwxrwxrwx   9 brian brian 4096 2005-10-13 06:18 hda5
drwxrwxrwx   3 brian brian 4096 2005-09-20 07:12 hda6
drwxr-xr-x  12 root  root  8192 1969-12-31 19:00 hdb1

```

My second drive is FAT32, and is mounted as read-only at /media/hdb1 for my user, but with full root access. This corresonds to my fstab, which is set up with default options:

```
brian@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0   1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda5       /media/hda5     ext3    defaults        0       2
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I don't know if it'd help, but since you seem to have done a couple of unusual temporary mounts, maybe a reboot would help, as an easy way to get rid of them.

---

### Post by likwid on 2005-10-16
> mark@hashbash:~$ ls -l /media
total 12
lrwxrwxrwx   1 root root    6 2005-10-16 11:54 cdrom -> cdrom0
drwxr-xr-x   2 root root 4096 2005-10-16 11:54 cdrom0
lrwxrwxrwx   1 root root    7 2005-10-16 11:54 floppy -> floppy0
drwxr-xr-x   2 root root 4096 2005-10-16 11:54 floppy0
drwxr-xr-x  11 root root 4096 2005-10-16 12:28 Media


Is what i seem to get. Also, i just tried knoppix bootcd to view the hdb1 contents and while the  top level folders and files are listed, they're all not accessible without root permissions. Browsing the mount as admin within ubuntu still works ok; i'm able to create new folders and open files. 

I'm troubled that fdisk reports hdb1 as ntfs. Is this definitely to be trusted? Disk tools does list the drive as ext3 and as root i can write to this partition. 

Thanks once again. I'm pretty gutted that i've spent so long on this today.

Edit: Obviously a problem where my partition isn't reported hdb1 from ls -l /media. ls -l media/Media displays the partition contents correctly. Is this maybe down to permissions?

---

### Post by likwid on 2005-10-16
I'm going to reinstall ubuntu and see what happens. Perhaps my initial mistakes when temp mounting to home folder, or to root of media is to blame. 

Thanks so much for your help. I'll post back to report on whether reinstall works out.

---

### Post by SilentCacophony on 2005-10-16
**EDIT** - Just saw the above post. If you are installing the 5.10 (Breezy) version, it should automatically mount all drives for you upon installation, whereas the 5.04 (hoary) version does not.


> I'm troubled that fdisk reports hdb1 as ntfs. Is this definitely to be trusted? Disk tools does list the drive as ext3 and as root i can write to this partition.
I can't say as I've ever heard of an ext3 partition being reported as NTFS by fdisk. I'm not sure why it would, or what would remedy it other than formatting it again, possibly. Sorry.

I have four ext3 partitions, and fdisk reports them as 'linux' on mine:

```
brian@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32
/dev/hda2             313         722     3293325   83  Linux
/dev/hda3             723        1338     4948020   83  Linux
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux
/dev/hda6            1852        2364     4120641   83  Linux
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA)

```

If it is actually ext3, I don't suppose it would hurt to try mounting it as ext3, and seeing if you could read from it. If you can read it as ext3, then it should be safe to write.

Other than these suggestions, I'm out of ideas.

---

### Post by likwid on 2005-10-16
Thanks mate for all your help, but i'm still stuck here.

Well. I'm absolutely gutted that i've spent a great many hours on this today and it's still not resolved. 

Having reformatted both drives, copied 180 gigs of media and reinstalled the OS i still do not have permissions to enter folders or files that have been mounted as normal user. I really don't know what else i can do. 

Is it because i'm formatting a slave as ext3 and copying data to it, then adding it to a OS installation once it is completed?

---

### Post by likwid on 2005-10-17
I thought i would get back to report the conclusion to my problems. There did seem to be some problem with the file system reportedly ntfs rather than ext3. This was resolved by second format. The further difficulty seemed to be that i was trying to import a media drive from another linux installation, and so the permissions were all screwed. Not sure why, but hey.

Thanks, SilentCacophony.

---

### Post by sitedesign on 2005-10-23
Here is my FSTAB file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    noatime,errors=remount-ro 0       1
/dev/sda5       /home           ext3    noatime         0       2
/dev/sda7       /media/data     ext3    noatime,rw,user         0       2
/dev/sda1       /media/windows  ntfs    ro,nls=utf8,umask=0000  0       0
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Pay attention to the line for /dev/sda7 which is my spare chunk of space which I use for video editing and large downloads etc (torrents).

The key element here is the rw, user part. This should tell the system to allow user to read and write to the partition. The noatime just makes the space a little quicker by not updating the access times every time files are read.

Remember to set the permisions on the folders as well.
chmod -R 777 /media/data
that lets everone full control over the contents of the contents of that partition. (use with caution) you may want to set the group permisions then put your user into that group instead. chown -R root:newgroup /media/data

Hope that helps.

---

