---
title: "fstab editing"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-12-09
New at this & have read/reread 2-3 tutorials, so need someone who knows better to look at my proposed fstab for errors of any type before I go ahead & possibly ruin a  perfectly good Dapper.
Thanks!

# /etc/fstab: static file system information.
#
# <file system> <mount point>  <type>     <options>                  <dump>  <pass>
proc            /proc           proc       defaults                   0       0
/dev/hda1       /               vfat       defaults,user,rw           0       0
/dev/hda5       /               ext3       defaults,user,rw           0       0
/dev/hda6       /home           ext3       defaults,user,rw           0       0
/dev/hda7       /               ext3       defaults,user,rw           0       0
/dev/hda8       /home           ext3       defaults,user,rw           0       0
/dev/hda9       /               ext3       defaults,user,rw           0       0
/dev/hda10      /home           ext3       defaults,user,rw           0       0
/dev/hda11      /               ext3       defaults,user,rw           0       0
/dev/hda12      /home           ext3       defaults,user,rw           0       0
/dev/hda15      /               reiserfs   defaults,user,rw           0       0
/dev/hda16      /               ext3       defaults,errors=remount-ro 0       1
/dev/hda17      /home           ext3       defaults                   0       2
/dev/hda18      none            swap       sw                         0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,exec,rw,noauto       0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,exec,rw,noauto       0       0
/dev/fd0        /media/floppy   auto rw,noauto,user,sync              0       0

---

### Post by lemonsCC on 2006-12-09
What are you trying to do with so many /home's?

---

### Post by halitech on 2006-12-09
ummmmmmm, how big of a drive do you have and why do you have a bunch of /home folders and / with different types of formating?

---

### Post by randiroo76073 on 2006-12-09
I have 6 distros installed + win98se, 1 distro=freespire=reiserfs.  As to number of partitions, each distro[except freespire] has a root & home, on a 120gb hdd.  I am assuming that win is a root partition, am open to critique & suggestions :)

---

### Post by ciscosurfer on 2006-12-09
> **randiroo76073 said:**
> New at this & have read/reread 2-3 tutorials, so need someone who knows better to look at my proposed fstab for errors of any type before I go ahead & possibly ruin a  perfectly good Dapper.
Thanks!

# /etc/fstab: static file system information.
#
# <file system> <mount point>  <type>     <options>                  <dump>  <pass>
proc            /proc           proc       defaults                   0       0
/dev/hda1       /               vfat       defaults,user,rw           0       0
/dev/hda5       /               ext3       defaults,user,rw           0       0
/dev/hda6       /home           ext3       defaults,user,rw           0       0
/dev/hda7       /               ext3       defaults,user,rw           0       0
/dev/hda8       /home           ext3       defaults,user,rw           0       0
/dev/hda9       /               ext3       defaults,user,rw           0       0
/dev/hda10      /home           ext3       defaults,user,rw           0       0
/dev/hda11      /               ext3       defaults,user,rw           0       0
/dev/hda12      /home           ext3       defaults,user,rw           0       0
/dev/hda15      /               reiserfs   defaults,user,rw           0       0
/dev/hda16      /               ext3       defaults,errors=remount-ro 0       1
/dev/hda17      /home           ext3       defaults                   0       2
/dev/hda18      none            swap       sw                         0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,exec,rw,noauto       0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,exec,rw,noauto       0       0
/dev/fd0        /media/floppy   auto rw,noauto,user,sync              0       0Your VFAT partition should not be mounted to root.  Here are a few links that will help you out:[LIST=1]
[*][http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows) (you can take a look at the rest of this site as well for assistance in other matters as well: [http://psychocats.net/ubuntu](http://psychocats.net/ubuntu) --particularly the sections about partitioning and what not)
[*][https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)[/LIST]

---

### Post by igknighted on 2006-12-09
When you put a mount point, it is not the moint point that OS would use.  Every partition needs its own.  I have on my SUSE install:
/debian/ubuntu for the ubuntu system
/debian/mepis for my mepis system
/debian/home for the home partition the above two share
/dream for my DreamLinux install
/gentoo for my Sabayon install

You should give each partition a unique mount point, or else the cyctem will get very confused, and this is not a good thing.  Also, you may need to manually create all of the folders (I used 'sudo mkdir /pathname').

---

### Post by randiroo76073 on 2006-12-09
ciscosurfer
Thanks
Will go back & reread psychcats again as I obviously missed that

ignighted
OK, in my mnt folder they are all listed by name[folder] ie: freespire, kubuntu-1r[root], kubuntu-2h[home], so I should use that for mount point?
Thanks

---

### Post by randiroo76073 on 2006-12-10
Hows this one?

# /etc/fstab: static file system information.
#
# <file system> <mount point>  <type>     <options>                  <dump>  <pass>
proc            /proc           proc       defaults                   0       0
/dev/hda1       /mnt/98me               vfat       defaults,user,rw           0       0
/dev/hda5       /mnt/pc-linux-1r               ext3       defaults,user,rw           0       0
/dev/hda6       /mnt/pc-linux-2h          ext3       defaults,user,rw           0       0
/dev/hda7       /mnt/mephis-1r               ext3       defaults,user,rw           0       0
/dev/hda8       /mnt/mephis-2h           ext3       defaults,user,rw           0       0
/dev/hda9       /mnt/kubuntu-1r               ext3       defaults,user,rw           0       0
/dev/hda10      /mnt/kubuntu-2h           ext3       defaults,user,rw           0       0
/dev/hda11      /mnt/kanotix-1r               ext3       defaults,user,rw           0       0
/dev/hda12      /mnt/kanotix-2h           ext3       defaults,user,rw           0       0
/dev/hda15      /mnt/freespire               reiserfs   defaults,user,rw           0       0
/dev/hda16      /               ext3       defaults,errors=remount-ro 0       1
/dev/hda17      /home           ext3       defaults                   0       2
/dev/hda18      none            swap       sw                         0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,exec,rw,noauto       0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,exec,rw,noauto       0       0
/dev/fd0        /media/floppy   auto rw,noauto,user,sync              0       0

---

### Post by ciscosurfer on 2006-12-10
I would change your VFAT line to look more like this: [B]
/dev/hda1 /mnt/98me iocharset=utf8,umask=000 0 0

[/B]Remember, though, that while you can mount your partitions to the /mnt directory, if you let the installer take care of this for you, they will show up in /media and will be easily accessible through your Places menu (as well as your Desktop).

This is also a good link to check out: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by randiroo76073 on 2006-12-20
ciscosurfer, thanks for tip re win. Although it would have been more convienent to have in media true, my grandkids are over occasionally so this is kind of my security idea, might have been another better way tho :)

---

### Post by ciscosurfer on 2006-12-20
> **randiroo76073 said:**
> ciscosurfer, thanks for tip re win. Although it would have been more convienent to have in media true, my grandkids are over occasionally so this is kind of my security idea, might have been another better way tho :)Any time! :KS

---

