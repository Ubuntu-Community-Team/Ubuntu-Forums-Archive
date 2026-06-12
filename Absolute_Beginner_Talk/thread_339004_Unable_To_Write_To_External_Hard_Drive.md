---
title: "Unable To Write To External Hard Drive"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by tsav87 on 2007-01-15
I am able to read the files on the external hard drive, but I am unable to write to it, it says i don't have permission to write.  I tried changing the permission in the properties, but it won't let me do that either.

If formatting it to fix it is a way to fix it, I can do that because there is nothing on it except a few things I used for windows that have no use to me anymore.

---

### Post by taurus on 2007-01-15
Is it ntfs or vfat/fat32 and how did you mount it?

---

### Post by jd65pl on 2007-01-15
Do you know what filesystem it is? Do the command below to determine this. Once the information is provided further help can be given.

```
mount -l
```

---

### Post by tsav87 on 2007-01-15
It is nfts.

It mounts via USP 2.0.  It shows up like my USB key, but I am unable to write to it.

---

### Post by tsav87 on 2007-01-15
> **jd65pl said:**
> Do you know what filesystem it is? Do the command below to determine this. Once the information is provided further help can be given.

```
mount -l
```

Here you go.

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/T-DRIVE type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8) [T-DRIVE]
/dev/sdc1 on /media/External Disk type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8) [External Disk]

```

---

### Post by Pobega on 2007-01-15
I just came across the same problem with my flash drive, and I used gparted to delete and recreate the partition; There is most likely an easier way, but that's how I did it.

**Edit:** If it's NTFS then forget what I said, NTFS is just hard to write to on Linux, but possible. I would personally consider converting it to a FAT32 or Ext filesystem though.

---

### Post by taurus on 2007-01-15
You cannot write to ntfs unless you use ntfs-3g driver!!!

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

Otherwise, format it as ext3 since Windows can read and write to ext2/ext3 now.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by tsav87 on 2007-01-15
How do I format it ext3?

---

### Post by Pobega on 2007-01-15
sudo aptitude install gparted
(Unless you already have it)

Run gparted and find your device in GParted -> Devices.

Then delete your currentl partition, right click the "unallocated" memory, and create a new partition using 100% of your memory (If that's what you want) as Ext3.

---

### Post by jd65pl on 2007-01-15
If you want compatability between windows and linux then format as FAT the filesystem is supported by both OSes for XRW permissions

---

### Post by Pobega on 2007-01-15
> **jd65pl said:**
> If you want compatability between windows and linux then format as FAT the filesystem is supported by both OSes for XRW permissions

I thought Ext was as well?

---

### Post by tsav87 on 2007-01-15
Should I make it a Primary or Extended Partition?

---

### Post by taurus on 2007-01-15
Primary.

---

### Post by karhulitos on 2007-01-17
Can't format fresh WD MyBook;
- Ubuntu 6.10
- WD MyBook 250GB USB disk
 Followed above instructions and installed GParted. Everything seems to go ok until (delete + unmount) I am to create a new partition, it asks for size and type, etc. I have selected all space, primary and ext3. Clicking add gives me new partition #1 and I hit apply.

GParted starts doing it's tasks but then opens the file explorer window in MyBook folder and GParted says:
"mkfs.ext3 /dev/sda1
/dev/sda1 is mounted; will not make a filesystem here!"

Tööt and that's it. Tried several times. I must be doing something wrong.. Please help!

(OMG, before hitting Submit I figured it out myself. It was System -> Settings -> Removable Drives/Media -> uncheck all auto mount options on that page. Writing this if someone lost 1h banging head on this)

---

### Post by tsav87 on 2007-01-17
The GParted worked great for my EXHD.  I had to restart before the changes took place though.

---

### Post by AceRimmer on 2007-01-18
Good tips, I'll have to give this a try if I have any problems with my new external disk.

---

### Post by tsav87 on 2007-01-18
Oh yeah, I forgot to mention.  To run GParted, after installing it, you have to type in this to get it to run.
```
sudo gparted
```

---

### Post by jd65pl on 2007-01-19
> **tsav87 said:**
> Oh yeah, I forgot to mention.  To run GParted, after installing it, you have to type in this to get it to run.
```
sudo gparted
```

Try this for running graphical applications with root access

```
gksudo *application*
```

---

### Post by Takuhari on 2008-01-31
I have a 500g hd.. 97%full...
deletion is not an option>_<

I took the time to install fuse and ntfs-3g
It is installed properly...
how am i able to use this?..

---

### Post by oedha on 2008-01-31
i am using NTFS and works fine....
go to system > administration > ntfs configuration tool
mark on both boxes

~E~

---

### Post by Takuhari on 2008-01-31
this is not an option in my administration tab

ntfs configuration tool

I manually installed ntfs-3g using: 
./configure 
make
make install

... i dont know if that makes a difference

---

### Post by oedha on 2008-01-31
i usually go to add/remove and search NTFS from all available applications
it still too hard for me to run the source code ( i am not confident yet :) )
then you'll have one
~E~

---

### Post by Takuhari on 2008-01-31
my system wouldnt find the packages for the ntfs...
so i had to install fuse via sourse and
ntfs3g via sourse&#12640;_&#12640;

it wasnt that hard... only 3 steps for each
but how to use it?..

on your dropdown list... is it between networking and printing?

---

### Post by oedha on 2008-01-31
yes...between those two
open it...mark on those two boxes.......

~E~

---

### Post by Takuhari on 2008-01-31
mines not there...
I dont know why...
It installed correctly and i can use it in the terminal... only if i knew how...:confused:

---

### Post by oedha on 2008-01-31
then sudo apt-get install ntfs-config

~E~

---

### Post by Takuhari on 2008-01-31
i get this...

> root@CrazyTacoCafeteria:/media# apt-get install ntfs-config
&#44984;&#47084;&#48120; &#47785;&#47197;&#51012; &#51069;&#45716; &#51473;&#51077;&#45768;&#45796;... &#50756;&#47308;           
&#51032;&#51316;&#49457; &#53944;&#47532;&#47484; &#47564;&#46300;&#45716; &#51473;&#51077;&#45768;&#45796;... &#50756;&#47308;
E: ntfs-config &#44984;&#47084;&#48120;&#47484; &#52286;&#51012; &#49688; &#50630;&#49845;&#45768;&#45796;
root@CrazyTacoCafeteria:/media#


it builds
&#50630;&#49845;&#45768;&#45796;... means not found...


I get that same prob when i was trying to find the ntfs-3g...
so i did it manually

---

### Post by oedha on 2008-01-31
do you have internet connction on that machine ?
what 's on your /etc/apt/sources.list ?
can you do sudo apt-get update ?

~E~

---

