---
title: "cdrom drive not working?? Help"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by klyver on 2007-07-06
When I try to open my cdrom drive I get the message:

Unable to mount the selected volume
mount: special device /dev/hda does not exist


Do I need to install a driver or something first?
It is a Samsung Combo cd/dvd rw, and it did work when I installed Ubuntu.

Anybody please help

---

### Post by MoxJet on 2007-07-06
Did you try mount /dev/dvd or /dev/cdrom ? Did you try sudo fdisk -l /dev/hda ?

---

### Post by klyver on 2007-07-06
thanks for the reply, but it doesn't work either.

klyver@klyver:~$ mount /etc/dvd
mount: can't find /etc/dvd in /etc/fstab or /etc/mtab
klyver@klyver:~$ mount /etc/cdrom
mount: can't find /etc/cdrom in /etc/fstab or /etc/mtab
klyver@klyver:~$ sudo fdisk -l /dev/hda
klyver@klyver:~$ 

this is what the fstab contains.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=235168d6-f5d3-4dea-97db-7053fc33a3c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d6bf28d0-c7ee-4e64-afa9-c203bce5dccf none            swap    sw              0       0
/dev/hda       /media/cdrom0   udf,iso9660 user,noauto     0       0


And this is what mtab contains.

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb1 /media/Flytbar\040Disk ntfs rw,nosuid,nodev,umask=222,utf8 0 0

---

### Post by dwblas on 2007-07-06
I might be hda, or hdb,  hdc or hdd are likely prospects.  Also note that it is /dev/drive not /etc/drive.  First try
mount /dev/hdc /media/cdrom0 
(assuming there is something in the drive that can be mounted.  You only mount data CD/DVDs, not video, music, etc.)
Next try hdd.  This will list all of your drives and lots of other info.  The first one listed is hda, second is hdb, etc. ignoring the sda drives.
sudo lshw -C disk

---

### Post by klyver on 2007-07-06
I've still got no success. Any more ideas?

klyver@klyver:~$ mount dev/hdc
mount: can't find dev/hdc in /etc/fstab or /etc/mtab
klyver@klyver:~$ mount media/cdrom0
mount: can't find media/cdrom0 in /etc/fstab or /etc/mtab
klyver@klyver:~$ mount dev/hda
mount: can't find dev/hda in /etc/fstab or /etc/mtab
klyver@klyver:~$ mount dev/hdb
mount: can't find dev/hdb in /etc/fstab or /etc/mtab
klyver@klyver:~$ mount dev/hdd
mount: can't find dev/hdd in /etc/fstab or /etc/mtab
klyver@klyver:~$ sudo lshw -C disk
  *-disk                  
       description: SCSI Disk
       product: Hitachi HTS54128
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: HP3O
       serial: HP2300BCGBG7PA
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 71GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 3153MB
          capacity: 3153MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 3153MB
             capabilities: nofs
klyver@klyver:~$

---

### Post by MoxJet on 2007-07-06
When you only add one parameter to mount, it checks it in mtab and fstab, as mounts tells you.

Do something like this instead
$ sudo mkdir /media/mnt
$ sudo mount /dev/dvd /media/mnt
and try some other:
$ sudo mount /dev/cdrom /media/mnt
$ sudo mount /dev/hda /media/mnt
$ sudo mount /dev/hdb /media/mnt
If it tells you to use a filesystem, just append -t iso9660, like this:
$ sudo mount /dev/hda /media/mnt -t iso9660

This works for me on computers with a bit odd hardware. Are you sure you have not done any hardware changes that led to the vanishing cd-rom-drive?

---

### Post by klyver on 2007-07-07
still no  luck

klyver@klyver:~$ sudo mkdir /media/mnt
klyver@klyver:~$ sudo mount /dev/dvd /media/mnt
mount: special device /dev/dvd does not exist

I get same response with cdrom, hda.....

I'm pretty sure I haven't done any changes that could have led to vanishing the cdrom drive, however during installation I had to use dpkg-reconfigure to find my graphics card. I did exactly as  described here [http://ubuntuforums.org/showpost.php?p=2754506&postcount=4](http://ubuntuforums.org/showpost.php?p=2754506&postcount=4) .
But when I used this tool I'm pretty sure I didn't get any questions about setting up my cdrom drive.

Any suggestions? and thanks for the so far

---

### Post by terrymor on 2007-07-07
I had a similar problem which drove me nuts for weeks. I finally fixed it by changing the jumper setting on the back of the drive from "cable select" to "master". Maybe that's your issue also.

---

### Post by klyver on 2007-07-08
well it's at laptop so thats difficult to check.... but I have also windows and the drive works in windows, so it must have something to do with the Ubuntu setup

---

### Post by klerbman on 2007-08-01
Having experienced the same issue (which led me to this site/thread) On a hunch I switched the bootup order in the BIOS.  I had CDROM first because of the install.  When I moved it to second and harddrive as first the problem resolved.

Feisty Fawn Server Installed on a Dell GX270

Regards,

klerbman

---

### Post by klyver on 2007-08-02
It didn't solve my problem, but thanks anyway

---

### Post by strBean on 2008-03-05
> **MoxJet said:**
> 
This works for me on computers with a bit odd hardware. Are you sure you have not done any hardware changes that led to the vanishing cd-rom-drive?

Hey - found an old thread to hijack - is that okay?  This is my first post.

This computer came with Ubuntu 6.06, installed and tested by cool folks at a Portland nonprofit called FreeGeek.  I'm pretty sure I remember it could talk to the CDR that came with it, but I immediately dropped a CDRW in along with it and now I get a message during bootup that loading hardware drivers failed, if that has anything to do with it, and also the following when I try to open the CDROM directory:
"mount: can't find /media/cdrom0 in /etc/fstab or /etc/mtab"

Would anybody like to walk a complete Linux idiot who has typed about 3 commands successfully in his life through a couple things to try?  I mean, you have to talk complete babytalk to me.  I know how to open the terminal and change a directory and I've copied a couple program launch commands and that's about it...

 thx

---

