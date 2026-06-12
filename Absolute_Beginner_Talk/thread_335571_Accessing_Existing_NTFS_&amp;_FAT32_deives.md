---
title: "Accessing Existing NTFS &amp; FAT32 deives"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2007-01-10
I have installed Ubuntu on a drive that has Windows XP and also have a USB drive I set up under XP.  I can see both via Linux and copy from these locations but cannot write to them.  Is this possible to do?

Thanks.;)

---

### Post by aidanr on 2007-01-10
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by play0r on 2007-01-10
you can easily write to FAT32 if you set the proper permissions for the drive. you can write to NTFS, but it's really flakey (mainly because it's still beta).
for the rare event i need to transfer something from linux<windows & vice versa, i just copy the data to a FAT32 partition & access the data from there.
here's a howto for writing to NTFS, but as i said before it's really flakey.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

good luck,
play0r

---

### Post by jgf621 on 2007-01-10
Thanks.  I did that but writing to it gives me a "You don't have permission" error.

---

### Post by finer recliner on 2007-01-10
to learn about bit permissions, read: [http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

### Post by bodhi.zazen on 2007-01-10
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by kencoburn on 2007-01-11
This worked for me (Ubuntu Dapper) on a sepate drive accessing Windows NTFS partition.

How to – Access Windows NTFS drive 

If you get the following message when trying to mount a NTFS partition:

Unable to mount the volume

error: device /dev/hda5 is not removable
error: could not execute pmount
You will need to download and install a program called ntfs-3g and do the following:

1.  Download and install ntfs-3g
ntfs-3g is not available (yet) via the Ubuntu package manager and so you will need to download ntfs-3g from a repository that was not included in the Ubuntu 'add/remove' programs list. 
Set up access to the relevant repository using:

sudo gedit /etc/apt/sources.list

and added the following line to the sources.list file:

deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main main-all

Use the Add/Remove / Advanced facility to install ntfs-3g.

2.  Obtain the Linux identity details for the NTFS drive(s)
Open a Terminal and enter:
sudo fdisk -l | grep NTFS
to display the NTFS drive information needed later.
/dev/hda2 * 911 7454 52564680 7 HPFS/NTFS
/dev/hda5 7455 30401 184321746 7 HPFS/NTFS
3.  Backup fstab file before modifying it
Now make a backup of the fstab file:
sudo cp /etc/fstab /etc/fstab.bak
4.  Amend fstab file to add details of NTFS drive obtained above
And then proceed to edit the original fstab file:
sudo gedit /etc/fstab

My fstab file ended up as follows (change highlighted):
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5       /media/windows  ntfs-3g defaults,local=en_GB.utf8 0 0

5.  Save fstab file and reboot
Save changes and reboot computer.  You should be able to access the NTFS partition.  In the case of Ubuntu an icon should appear on the Desktop.

I got the information from this forum.  I hope that helps.

---

### Post by blakeforeman on 2007-01-14
i have a similar question, i am trying to acess files off of an ntfs winows network ......is there a way to do this of i am in the wrong place for this just link me to where someone can help me.

---

### Post by bodhi.zazen on 2007-01-14
> **blakeforeman said:**
> i have a similar question, i am trying to acess files off of an ntfs winows network ......is there a way to do this of i am in the wrong place for this just link me to where someone can help me.

I think you might try samba:

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

[http://wiki.linuxquestions.org/wiki/Samba](http://wiki.linuxquestions.org/wiki/Samba)

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by jgf621 on 2007-01-16
This issue was solved nicely when I followed instructions at

:-D  [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

---

### Post by Elim on 2007-01-17
> **bodhi.zazen said:**
> Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

Why does one need to set permissions?  I've successfully mounted an ntfs drive (read-only) but I've yet to dicker with the permissions, and thus far I haven't had trouble accessing it.  Is setting the permissions necessary?

---

### Post by bodhi.zazen on 2007-01-17
> **Elim said:**
> Why does one need to set permissions?  I've successfully mounted an ntfs drive (read-only) but I've yet to dicker with the permissions, and thus far I haven't had trouble accessing it.  Is setting the permissions necessary?

Setting permissions is not necessary if it is working the way you like :)

Permissions are used to:[list=number][*]give read-write access
[*]restrict access (security).[/list]

---

### Post by Elim on 2007-01-17
Now I'm not so sure...  *laughs*  Because of this thread I started thinking about the issue.  I realized that I'm going to be mounting this ntfs partition as well as a data ext3 partition, and I want to be able to access them myself but have *no* access (either read or write) to either partition by any other users.  So I need to figure out the options to use, but I'm having trouble figuring out umaks/fmask/dmask.

Then it occurred to me that I could use uid=me and be done with it.  Can I?  If so, why does [_[COLOR="RoyalBlue"]this[/COLOR]_](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-2a64a964ff8833576586c7216a1199f022c505a6) use both uid and fmask/dmask?

Also, I don't suppose you'd happen to have a link explaining u/f/dmask?  I'm still not sure how it works, really.

---

### Post by bodhi.zazen on 2007-01-17
> **Elim said:**
> Now I'm not so sure...  *laughs*  Because of this thread I started thinking about the issue.  I realized that I'm going to be mounting this ntfs partition as well as a data ext3 partition, and I want to be able to access them myself but have *no* access (either read or write) to either partition by any other users.  So I need to figure out the options to use, but I'm having trouble figuring out umaks/fmask/dmask.

Then it occurred to me that I could use uid=me and be done with it.  Can I?  If so, why does [_[COLOR="RoyalBlue"]this[/COLOR]_](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-2a64a964ff8833576586c7216a1199f022c505a6) use both uid and fmask/dmask?

Also, I don't suppose you'd happen to have a link explaining u/f/dmask?  I'm still not sure how it works, really.

focl (fell off chair laughing).

Best source of information is man mount: [http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

> uid=value and gid=value
    Set the owner and group of all files. (Default: the uid and gid of the current process.) 
umask=value
    Set the umask (the bitmask of the permissions that are not present). The default is the umask of the current process. The value is given in octal. 
dmask=value
    Set the umask applied to directories only. The default is the umask of the current process. The value is given in octal. 
fmask=value
    Set the umask applied to regular files only. The default is the umask of the current process. The value is given in octal.

umask is the opposite of permissions used in chmod.

For full access:

chmod 777 = umask 000

Access control varies depending on the file system you mount.

In general for windows (fat/ntfs) use uid = you and gid = you umask=077 (access for you only)

In general for linux (ext3, reiser, JFS, XFS)

use:
```
chown you:you (that's user:group) directory
chomd 770 directory
```

with the directory mounted.

u/d/f mask gives finer control but you likely only need umask :)

HTH

---

### Post by Elim on 2007-01-18
^ Most helpful, as always, bodhi.  And yet I still have problems...

I successfully mounted and then chowned and chmoded the ext3 data partition, and its working well--no other users can access it.  Unfortunately, the same can't be said of my Windows partition, which is still accessible by all users.  Here's what I put in fstab:

```

/dev/sda1    /mnt/windows    ntfs    nls=utf8,fmask=0377,dmask=0277,uid=1000     0     0

```

So, I would think that with the above in fstab I'd be the only one that would be able to read the Win partition, but when I log in to another user account that I created for testing this the other user can access it, too.  Any ideas?

---

