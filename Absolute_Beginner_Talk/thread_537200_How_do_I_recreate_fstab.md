---
title: "How do I recreate fstab?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Paideuma on 2007-08-28
This is my first post.  I looked through existing posts and couldn't find anything that matched my problem...

I overwrote fstab when trying to mount something.  I typed:

sudo cp *.bin /etc/fstab

I didn't realize fstab was a file, I thought it was a directory.  Well, obviously, now my fstab is corrupted.  I haven't yet restarted my computer and everything seems to be working fine for the moment.  What can I do to restore or recreate my fstab file?

:\

---

### Post by wjp.reg on 2007-08-28
did you check the /etc folder for a backup of fstab which the system might have created?

---

### Post by s26c.sayan on 2007-08-28
You can always hand-edit the file depending on your system partitions!

Also, I* think* you can use the ubuntu (or another) Live CD which auto-generates a fstab for the live-session, which you can copy over the corrupted file on the hard disk.

---

### Post by Paideuma on 2007-08-28
> **wjp.reg said:**
> did you check the /etc folder for a backup of fstab which the system might have created?

The only file in the /etc directory with the name fstab in it is "fstab.pre-uuid."

---

### Post by Paideuma on 2007-08-28
> **s26c.sayan said:**
> You can always hand-edit the file depending on your system partitions!

Also, I think you can use the ubuntu (or another) Live CD which auto-generates a fstab for the live-session, which you can copy over the corrupted file on the hard disk.

The file no longer opens up in gedit, but being as it's now 136.5 MB due to my mistake, I don't think its editable.

I'll try the Live CD thing, any suggestions as to how I should go about it?

---

### Post by bodhi.zazen on 2007-08-28
Open you terminal

use fstab.pre-uuid as a template

In a terminal use the commands :

```
sudo mount # will list your current mounted file systems
blkid # will list your devides by UUID
```

See this as a reference :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Here is a "basic" template :

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=957439b4-aec7-47de-b8a5-940931956b8d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=7da0c203-4ef9-491c-9215-add3ba009b7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

oic you posted as I was typing.

You need to open the file as root :

```
gksu gedit /etc/fstab
```

IMO it will be just as easy to fix it without re-booting

---

### Post by s26c.sayan on 2007-08-28
> **Paideuma said:**
> The only file in the /etc directory with the name fstab in it is "fstab.pre-uuid."

I think before anything else, you can just try :

sudo cp /etc/fstab.pre-uuid /etc/fstab

In my system, both the files looks same, so you might be in luck!! :)
You may need to add any modifications you had made (if any) to the end of thenew fstab...but I doubt if you'll need that!

---

### Post by ajgreeny on 2007-08-28
In my setup the pre uuid version is an almost empty file which says simply "# UNCONFIGURED FSTAB FOR BASE SYSTEM" so there would be no point copying that if your version is like mine.

I suggest you forget about the uuid of the disks etc and simply go back to the device nomenclature, eg /dev/hda1 or /dev/sda1 etc etc for the partitions you want.  Have a look at this site, [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) which has a lot of info about the file makeup and how it is used.  It may be very helpful to you as you can find all your partition dev names with that by typing sudo fdisk -l in terminal and noting the linux and windows partitions you want mounted at boot time.

Just for info here is my fstab, which I have edited so that windows does not mount at boot up, neither does my second linux install, I just mount them if I need with aliases in the .bashrc file in my home folder.  I'm pretty sure you must have the proc line as it is here, and as long as you get the dev names right you can certainly dispense with the uuid of partitions etc.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2  /               ext3    defaults,errors=remount-ro 0       1  **My ubuntu**
# /dev/hda1  /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1  **My Windows**
# /dev/hdb1  # /media/hdb1     ext3    defaults        0       2  **My Linux Mint**
/dev/hda5  none            swap    sw              0       0  **Ubuntu swap**
#/dev/hdb5  none            swap    sw              0       0  **Mint swap**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Good luck.

---

