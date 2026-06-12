---
title: "Cannot mount volume"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by diomedesxx on 2008-01-30
Hi,
I received the following message when I inserted a CD, I believe it is a data disc, no music. I have not had a problem in the past with audio or data CD, or DVDs.

The message
```
mount: block device /dev/hda is
write-protected, mounting read-only
mount: Not a directory
```

lshw -C disk
```
diomedesxx@diomedesxx-desktop:~$ sudo lshw -C disk
  *-disk:0                
       description: SCSI Disk
       product: SAMSUNG HD160JJ/
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: ZM10
       serial: S0DFJ1CLC12579
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: ST3750640AS
       vendor: ATA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 3QD0AH6Z
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: ATAPI DVD A DH16AYH
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: YH13
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
     *-disc
          physical id: 0
          logical name: /dev/hda
```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6b58a1c9-f802-4b69-a7c8-d19a25a1f728 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=182CAE322CAE0AB8 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=2C88743C8874071C /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=0c6c6db7-13e7-4b7a-9591-abadc9103b21 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I'm not quite sure what to do at this point, if someone could point me in the direction it would be much appreciated.

---

### Post by cleverselfreferentialname on 2008-01-30
It's supposed to do that. :-)

---

### Post by jeffus_il on 2008-01-30
The line in fstab looks fine, why not try comment it out, because removable media can be mounted by gnome without the fstab line.

---

### Post by diomedesxx on 2008-01-30
I received the same error, just missing the "mount: Not a directory" :(

---

### Post by jeffus_il on 2008-01-30
Ok, Can you access the CD through Nautilus or a desktop icon?
What is the output of ```
mount
``` in a terminal?

---

### Post by diomedesxx on 2008-01-30
output ```
diomedesxx@diomedesxx-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/HDD type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

After I receive the error, an icon does not appear, and I cannot browse to it through Nautilus.

---

### Post by _mOrgoth_ on 2008-01-30
I hope this helps..
[http://ubuntuforums.org/showthread.php?t=545938](http://ubuntuforums.org/showthread.php?t=545938)

---

### Post by diomedesxx on 2008-01-30
Unfortunately that reference did nothing to help, I still receive the same error.

---

### Post by dcstar on 2008-01-30
> **diomedesxx said:**
> Hi,
I received the following message when I inserted a CD, I believe it is a data disc, no music. I have not had a problem in the past with audio or data CD, or DVDs.

The message
```
mount: block device /dev/hda is
write-protected, mounting read-only
mount: Not a directory
```
........
fstab
```
# /etc/fstab: static file system information.
.......
/dev/hda        **/media/cdrom**0   udf,iso9660 user,noauto,exec 0       0
```

I'm not quite sure what to do at this point, if someone could point me in the direction it would be much appreciated.

Check your /media directory and make sure that **cdrom0** exists in it, if not then you can create a folder with that name (make the owner/permissions the same as the other folders there).

Here is what is in my system:
```
lrwxrwxrwx  1 root root       6 2007-10-16 03:59 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2007-10-16 03:59 cdrom0
```

---

### Post by diomedesxx on 2008-01-30
unfortunately, I do have a folder by the name cdrom0 and the permissions are the same as the other files in my /media directory

---

### Post by dstew on 2008-01-30
I think you need to use a partition and not a disk name. /dev/hda is a disk name. You need to specify a partition, like /dev/hda1. My fstab line for my cd rom is ```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by jordanmthomas on 2008-01-30
Your problem is that /dev/hda is the disk itself, not a partition on the disk.  You can not mount a physical disk.

edit
woops, someone just said that. :)

---

### Post by diomedesxx on 2008-01-31
> **dstew said:**
> I think you need to use a partition and not a disk name. /dev/hda is a disk name. You need to specify a partition, like /dev/hda1.

That made me feel like an idiot, but the error still persists, though I've changed the entry for < file system > to match that of the partition it will mount to. The only difference is now on the error message, the last line that had a carriage return to appear on the third line starts on the second line of the error box and spills onto the third. :confused:

---

### Post by oedha on 2008-01-31
have you put the line like dstew #11 said onto your /etc/fstab ?

~E~

---

### Post by diomedesxx on 2008-01-31
yup ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6b58a1c9-f802-4b69-a7c8-d19a25a1f728 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=182CAE322CAE0AB8 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=2C88743C8874071C /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=0c6c6db7-13e7-4b7a-9591-abadc9103b21 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by jordanmthomas on 2008-01-31
You're trying to mount /dev/sda2 as a cd because you have chosen the filesystem iso9660.

Are you sure this is what you want?  Odds are /dev/sda2 is not a cd as it is already mounted as /.

---

### Post by diomedesxx on 2008-01-31
this is the output of my lshw ```
              *-cdrom
                   description: DVD-RAM writer
                   product: ATAPI DVD A DH16AYH
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: YH13
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hda

```

So I should change "/dev/sda2" to "/dev/hda"? If that is the case, it puts me back to square one with the error message.

---

### Post by jordanmthomas on 2008-01-31
Reading through the thread, your problem seems a little strange.
It DEFINITELY shouldn't be /dev/sda2 you have there.

Earlier, when I said that /dev/hda is the disk itself I assumed you were referring to a hard drive and not your DVD drive (my mistake, sorry) and in fact you SHOULD put /dev/hda there.

Try using auto instead of udf,iso9660
```
/dev/hda       /media/cdrom0   auto user,noauto     0       0
```
See if that helps any.

---

### Post by dstew on 2008-01-31
This is an interesting problem. I think it has to do with how the cdrom is claimed during the kernel boot up. On [this page]("http://tldp.org/HOWTO/SCSI-2.4-HOWTO/sr.html"), in section 9.2.4, it goes into a technical discussion of this. It seems that your cdrom (DVD drive in your case) is an ATAPI drive, and is being claimed by the ide device /dev/hda. I will study this a bit more and try to get some idea on how to get it claimed by the (correct) scsi device.

EDIT: A quick thing to try is add **hda=ide-scsi** to the kernel boot line in /boot/grub/menu.lst
EDIT no. 2: Also, try **modprobe ide-cd ignore='hda'**

---

