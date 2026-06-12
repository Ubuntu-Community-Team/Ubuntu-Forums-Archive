---
title: "Mounting my NTFS partition"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by anoncompboy on 2005-12-23
I am trying to mount my windows NTFS partition, read only of course, using an official doc site. I know I am doing it the right way, but when I do it i get the message "mount: only root can do that"

I think root is the equivelent of admin in the windows user system. So how do I log into root?

---

### Post by cstudent on 2005-12-23
If you are using the terminal and entering commands, you can activate root by using the sudo command before everything else.

Example:

sudo apt-get update

It will ask you for YOUR password the first time it's called. The root permission is active for about 15 minutes. So it won't ask again until that time runs out. But you have to put the command in for every command you want done as root.

EDIT:

If you want to do it the GUI way in Ubuntu (Gnome) with a duel boot setup. Go to the Systems menu>Administration>Disk. Click on your Windows disk and select the partitions tab. Enter in the access path box /media/windows and then click the enable button. You may have to create the /media/windows directory first. I can't remember if it asked me or not when I done mine the first time. If you should have to. Open a terminal window and enter:

```

sudo mkdir /media/windows

```

---

### Post by aysiu on 2005-12-23
See the fourth link of my sig.

---

### Post by anoncompboy on 2005-12-23
Thanks cstudent and aysiu.

Okay, heres what happened, the GUI system/admin/disk is worthless. I tried it, it cant mount anything, hit the buttons and they just flicker. Guess its just a gimmick to try and make ubuntu look user-friendly. However, followed a good article and got my windows NTFS partition mounted correctly.

Now, I go into it and it says I dont have permissions to view it. I have also noticed I can't delete or rename anything. I have gone into system/admin/users and given myself all permissions. I am the only user on the OS, I am admin, so "permissions" shouldnt even exist until I create a second user. Ok, so wheres the magic button to fix this?

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=anoncompboy]I am trying to mount my windows NTFS partition, read only of course, using an official doc site. [/QUOTE]
but
[QUOTE=anoncompboy]I have also noticed I can't delete or rename anything.[/quote]

==> read-only means all you can do is read it, you cannot change anything on your ntfs partition...

about permissions: did you do this part of aysiu's link? it's meant to address that issue > This is what it might look like before we change it:```

proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
**/dev/hda1 /media/hda1 ntfs defaults 0 0**
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
```

This is what it should look like after we change it:```

proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
**/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0**
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0 
``` 

---

### Post by anoncompboy on 2005-12-23
oops, I see I wrote that wrong. I meant I can't rename/delete in other folders like my /media directory where I am trying to mount other drives; I cant even attempt to change files in my NTFS mount because I can't view it. I am not interested in writing to my NTFS partition, i just need to get past privelages so I can view it and change files elsewhere.

---

### Post by eZtaR on 2005-12-23
I also tried to mount some ntfs partiotions but when i do the sudo mount -a i get this

```

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```


And when i do dmesg | tail i get this
```

NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.

```

---

### Post by PsychoTrauma on 2005-12-23
Did you install libntfs5 from the repos?

```
sudo apt-get install libntfs5
```

---

### Post by eZtaR on 2005-12-23
[QUOTE=PsychoTrauma]Did you install libntfs5 from the repos?

```
sudo apt-get install libntfs5
```[/QUOTE]

Now i did but i still get the error

---

### Post by PsychoTrauma on 2005-12-23
[QUOTE=eZtaR]Now i did but i still get the error[/QUOTE]

Could you post your fstab? Installing libntfs5 allows ntfs partitions to be read since by default the can't be.

---

### Post by eZtaR on 2005-12-23
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2 /d ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /e ntfs nls=utf8,umask=0222 0 0

```

---

### Post by hydravien on 2005-12-23
i am also having the same problem trying to get it to work...

heres my fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /windows     ntfs    nls=utf8,unmask=0222        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sdb2       /media/sdb2     vfat    defaults        0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0







              [ line 2/13 (15%), col 1/46 (2%), char 1/676 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

```

---

### Post by PsychoTrauma on 2005-12-23
First I would recommend you doing:

```
sudo mkdir /media/d
```

```
sudo mkdir /media/e
```

then changing your fstab lines to:

```
/dev/hda2 /media/d ntfs umask=0222 0 0
```

```
/dev/hdb1 /media/e ntfs umask=0222 0 0
```

I think your problem is your trying to mount something in /e-/d.

---

### Post by PsychoTrauma on 2005-12-23
[QUOTE=hydravien]i am also having the same problem trying to get it to work...

heres my fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /windows     ntfs    nls=utf8,unmask=0222        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sdb2       /media/sdb2     vfat    defaults        0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0







              [ line 2/13 (15%), col 1/46 (2%), char 1/676 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

```[/QUOTE]

I think you are having the same problem. So in your case do:

```
sudo mkdir /media/windows
```

and change the ntfs line to:

```
/dev/hda2       /media/windows     ntfs    umask=0222        0       0
```

---

### Post by eZtaR on 2005-12-23
I still get the same error :(

---

### Post by hydravien on 2005-12-23
yup

---

### Post by hydravien on 2005-12-23
okay after messing around some more, it seems to let me mount, then say 

error you do not have the permissions necessary to view this drive...

---

### Post by PsychoTrauma on 2005-12-23
Open the gnome disk manager and make sure you are pointing the fstab at the correct partiton. For example on my fstab my windows drive is on /dev/hdb1 because it's another hard drive.

hydravien make sure you did umask=0222 and not unmask=0222.

---

### Post by hydravien on 2005-12-23
hah i succeeded 
i went to disks manager and tried it....

now it works

now i will reboot and see if it will continue to work

---

### Post by eZtaR on 2005-12-23
[QUOTE=PsychoTrauma]Open the gnome disk manager and make sure you are pointing the fstab at the correct partiton. For example on my fstab my windows drive is on /dev/hdb1 because it's another hard drive.

hydravien make sure you did umask=0222 and not unmask=0222.[/QUOTE]

And what if i'm a KDE user?

---

### Post by PsychoTrauma on 2005-12-23
Control center will probably have the information you're looking for but i'm not sure since I only occasionally play with kde. You're just checking to make sure the windows partitons are where you think they are (/dev/hda2,/dev/hdb1).

---

### Post by eZtaR on 2005-12-24
[QUOTE=PsychoTrauma]Control center will probably have the information you're looking for but i'm not sure since I only occasionally play with kde. You're just checking to make sure the windows partitons are where you think they are (/dev/hda2,/dev/hdb1).[/QUOTE]
Thanks dude :) I'm now up and running.. Now i all i need to do is reformat my drives to fat32, get mp3 playback to work and get cedega up and running :D

---

### Post by brummieman on 2005-12-24
Well I read this thread with interest.  I have used various flavours of Linux (redhat, Mandriva, SUSE) and I must say I am struggling a bit with this one (despite hardware detection being the best I have found - even my G WiFi worked straight off !!! :p ).

My NTFS data disks (3 of them) are not automatically mounted as they were in other distros.  I want read and write access to them.

Is it possible in Unbuntu 5.10 X64?

I tried to use the admin/disk manager, first i couldn't get them to mount at all, then they mounted as / and I couldn't disable them :( 

How do I get them to show as disk drives on the desktop (as i had them in Mandriva) ?

Sorry for the newbie question...but this distro seems one of the best I have seen and I want to use it productively (difficult when I onlyt currently have write access to the boot disk - a small 10GB disk I use for Linux)

Thanks
Brummieman

---

