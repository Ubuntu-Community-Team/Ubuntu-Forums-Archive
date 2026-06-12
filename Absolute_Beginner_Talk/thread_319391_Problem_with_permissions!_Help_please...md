---
title: "Problem with permissions! Help please.."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-12-15
Hey all

I experienced some problems earlier with permission to write to, among others, my /usr - folder.. Then I did it through "sudo nautilus," worked fine, didn't think any more about it. I then purchased an portable HDD. It has been working fine until today, when suddenly (and I mean suddenly. From one second to the next) I wasn't allowed to write to the HD anymore.. Every time I try to change the permissions - settings, I get the message that I am not allowed to do it, and that my HDD is a "read - only" - device, which it most definetly_not_is! It doesn't work with "sudo nautilus" either. So I have 300 Gb of unusable storagespace unless I get to fix this. Everything I already have on the HDD is working, and most of it is there. Lost some things, though. 

I am thinking there is a serious permissions-problem within nautilus? Which developed from affecting my /usr - folder and all other system - files, to bothering me and my portable HDD.. I tried the HDD on my girlfriends windows - box, there it worked fine! So there is nothing wrong with the HDD itself, there is no copy-saftey on it. It is an Iomega 320 Gb, btw. In windows it worked just the way it is supposed to, except for the files that were damaged somehow when this happended. 

I am using Gnome/Dapper/686 - but have also XFCE - desktop installed, used extensivly for quite some time, but back to Gnome now. XFCE - desktop is still installed, though. Haven't tried it in XFCE, but see no reason it should work there seeing as it is the same system? Or is it a possibillity that it works in XFCE. Anyways, it worked fine in Gnome for quite some time, so something has happened to it today. 

any help will be rewarded with big, sloppy kisses...

lodravah

---

### Post by lodravah on 2006-12-15
Update:

Tried mounting the external HDD using Ubuntu LIVE - CD. Was able to read, but had the same issues when wanting to write to it: "Not permission to write" or "read only!" This is bulls**t... I'm really getting frustrated here! Tried different kinds of approaches found on the forum.. Editing etc/fstab, no luck! I'm not even allowed to do anything as root in "sudo nautilus!" 

Some additional info!

@lodravah:~$ fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    b  W95 FAT32

And:

@lodravah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
@lodravah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

The external HDD is an Iomega 320 Gb. It worked fine until suddenly snapped into "permisson denied - mode!" 

From Terminal - when running sudo - nautilus:

lodravah:~$ gksudo nautilus
(nautilus:5308): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:5308): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(nautilus:5308): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (nautilus:5308): CRITICAL **: nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed


I'm outta ideas, and need help..!

lodravah

---

### Post by po0f on 2006-12-15
lodravah,

I don't see an entry for your removable drive in the /etc/fstab you posted.  Are you sure you tried everything?  vfat filesystems need to be mount with umask=000 to be world-readable/writable.  Try something like this (when it's plugged in):
```
[FONT="Courier New"]$ sudo mount -t vfat -o umask=000 /dev/sda1 /media/data[/FONT]
```

---

### Post by thelinuxguy on 2006-12-16
> The external HDD is an Iomega 320 Gb. It worked fine until suddenly snapped into "permisson denied - mode!" 

You are saying your drive was WRITABLE before this thing happened. When I installed Ubuntu my windows partitions were not writable. I tried changing the mask to 000  in fstab and even changing permissions but could not write to those partitions. The default NTFS kernel drivers MAY have write capability disabled. Then I installed the ntfs-3g drivers and now have full acess. Detailed instructions are  [here]("http://www.ubuntuforums.org/showthread.php?t=217009").

Your problem seems to be slightly different since u were able to write to it before. But u could give this a try.

My fstab looks like this

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda11      /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/win_c     ntfs-3g    defaults	0       1
/dev/sda5       /media/win_e     ntfs-3g    defaults	0       1
/dev/sda6       /media/win_f     ntfs-3g    defaults	0       1
/dev/sda7       /media/win_g     ntfs-3g    defaults	0       1
/dev/sda8       /media/win_h     ntfs-3g    defaults	0       1
/dev/sda9       /media/win_i     ntfs-3g    defaults	0       1
/dev/sda10      none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by lodravah on 2006-12-16
The fstab is for static file systems only. Does it work with removable HDD's? 

sudo mount -t vfat -o umask=000 /dev/sda1 /media/data

Result:
@lodravah:~$ sudo mount -t vfat -o umask=000 /dev/sda1 /media/data
mount: mount point /media/data does not exist

lodravah@lodravah:~$ sudo mount -t vfat -o umask=000 /dev/sda1 /media
mount: /dev/sda1 already mounted or /media busy
mount: according to mtab, /dev/sda1 is mounted on /media/IOMEGA_HDD
lodravah@lodravah:~$ sudo mount -t vfat -o umask=000 /dev/sda1 /IOMEGA_HDD
mount: mount point /IOMEGA_HDD does not exist

lodravah@lodravah:~$ sudo mount -t vfat -o umask=000 /dev/sda1
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Umask 000 did not work. Will a complete Ubuntu-reinstall work? I first started having permission-problems in editing in /usr - folder. It used to work with copy/paste, then suddenly it didn't anymore. Like changing "distributor-logo.png" in /usr/share/pixmaps etc. etc. Then suddenly I had to go to root via "sudo nautilus" to do changes in /usr. Is this a sign of something else wrong? I think the permissions - problems started when I transferres my mp3's to the HDD. It was the last change I did before the problems started..

@ linuxguy: my external HDD is FAT32, and I have no desire to change it to nfts since FAT32 works fine with Win and linux, and the fact that the HDD_was_working fine until something suddenly happened!

---

### Post by lodravah on 2006-12-16
And also, in the HDD - "properties" my name is listed as owner, and all the read/write/execute - boxes are ticked..

---

### Post by lodravah on 2006-12-16
*bump*

---

### Post by scooter3k on 2007-05-11
the exact same thing happened with me.  has anyone found a solution to this?

its really weird...i have a usb external hd, FAT32 also...right after i mount it, i can write to it for about 5 or 10 seconds...then, all of a sudden it just stops letting me.  dont know why.  if i try to write to it, it gives me the: Error "Read only file system"

any idea why it is mounting as read/write then after about 10 seconds changing to read only?

thanks in advance :)

---

### Post by lodravah on 2007-05-15
Sorry for the delay in answer. 

I'm sorry, but I didn't find any solution. What I had to do was move all my files to another HDD, then reformat my own HDD using a Win - app called Partition Magic, or something like that. Used my neighbourd PC for that. Formated fresh in FAT32. After that, it has been working like a charm. I spent quite a lot of time trying to figure it our, but had to give up in the end. But just to be curious, what kind of portable HDD are you using? Mine is a 250 Gb Iomega.

---

### Post by scooter3k on 2007-05-16
280 gb fantom drives.

really sucks though...

i think it started happening one time when i loaded files to it via ftp, and one of them got corrupt somehow.  probably a stupid theory...but maybe someone will know more than i do about it.  i knew the file was corrupt b/c when i plug it into a windows pc and try to copy it over, i got the segmentation fault error.

thanks for responding anyway :)

---

### Post by lodravah on 2007-05-16
Does it work in Win? Because my did, so the problem is isolated to Ubuntu. I think it was something of tjhe same problem I had. I was transferring mp3's to the HDD, and one of the files were corrupt and dragged the whole HDD down with it. I was looking for a solution for a long time. The only thing I can suggest is to use a Win-PC to transfer and keep the files you want, and then try to reformat it. Either in ext3 or FAT32 for use with Win-machines..

---

