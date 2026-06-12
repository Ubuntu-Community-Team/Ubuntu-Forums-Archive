---
title: "fstab config"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by andry1 on 2006-09-23
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,sync  0       0


this is my actual fstab config! when i use the mount command, shows this error: 
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i can access my windows drive, but my other drive with documents and music wich is in fat32 system, i can't access.. can u help me?
thx

---

### Post by djsroknrol on 2006-09-23
You might try this:

```
/dev/hdb1 **/media**/fat_files vfat iocharset=utf8,umask=000 0 0
```

I think the item in bold is missing and that might be the problem....hope it helps...

---

### Post by andry1 on 2006-09-23
trying to do as you say appears this message:
mount: mount point /media/fat_files does not exist

but i've read an article about mounting, and from what i've read i tried to apply it. so changing to 
/dev/hdb1 /fat_files vfat user,iocharset=utf8,umask=000 0 0
i can access the drive, but in the terminal as root. either in my user, or in graphical mode i still cant access it :confused:

---

### Post by Average Joe on 2006-09-23
What if you mount it in fstab like:
```
/dev/hdb1       /fat_files        vfat    defaults,utf8,uid=1000,fmask=0133,dmask=0022    0       0
```
And type:
```
sudo mount -a
```
after editing the /etc/fstab file?

That should give you access to your fat files if you go to the /fat_files directory in Nautilus. (With these permissions they are readable for everybody, but only writeable for you.)

---

### Post by andry1 on 2006-09-23
i still cant mount the drive:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
that was the error from the beggining

---

### Post by Average Joe on 2006-09-23
Maybe your /dev/hdb1 is not a vfat partition, but just trying to be mounted like that in your fstab? I can image things go wrong then.

Maybe you could check your /dev/hdb1 partition for the right partition type and errors. I am not sure how to do that though. What does:

```
sudo fdisk -l
``` give you for /dev/hdb1? Still vfat or something else?

EDIT: My partition mounted as vfat gives W95 FAT32 (LBA) as a system in the fdisk -l output.

---

### Post by andry1 on 2006-09-23
guess i was mistaken :oops: 
 a friend of mine solved the problem for me.. i was 99% sure that my drive was in fat system.. i never formated that hd, so i cant guess how that changed into ntfs system, except that i looks like it's me who's done it.. the computer cant have changed for itself! :p sorry for the trouble man..

---

### Post by pod25 on 2006-09-23
> **andry1 said:**
> i still cant mount the drive:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
that was the error from the beggining
If you go to System/Drives , then select the drive you are trying to mount, it will tell how that drive has been formatted.
Then using terminal :
```
mkdir /media/windows
```
then
```
sudo nano /etc/fstab
```
add these lines (if not already there)
```
/dev/hdb1 /media/windows  ntfs nls=utf8,umask=0222 0 0
```
or
```
/dev/hdb1 /media/windows vfat iocharset=utf8,umask=000 0 0
```
Then press ctrl/o to save and ctrl/x to exit

Then reboot.

---

### Post by djsroknrol on 2006-09-23
I'm so sorry....forgot to even mention mounting the partition, but I see something else now on second inspection that is a problem...the underscore in "fat_files" is the reason for the illegal action message....

If you name the partition anything else, it will mount without incident.

---

