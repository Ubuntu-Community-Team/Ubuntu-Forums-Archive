---
title: "No Thumbnails in Nautilus Edgy"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by daz4126 on 2006-11-06
Hi,

After upgrading to Edgy, Nautilus will not display thumbnails of images. I have tried going to edit -> Preferences -> Preview and selected the option to show thumbnails for local files only, but it just shows a generic image for all images in any folders. Anybody got any ideas how to fix this?

thanks,

DAZ

---

### Post by jdpipe on 2007-02-22
I've got this problem too. I have ubuntu installed on a USB hard drive and I notice that on some machines the thumbnails show and on others they don't. Could it be some kind of conditional configuration thing depending on the video card or CPU speed etc?

Cheers
JP

---

### Post by ^rooker on 2007-02-22
you did check the filesize of the affected files?

You can configure to produce previews only if files are below a certain size....

---

### Post by jdpipe on 2007-02-22
Yeah, no, that's not the problem. Even small PNGs are not being thumbnailed.

---

### Post by orb9220 on 2007-02-22
Try running a gksudo nautilus it might be permissions thing.

I have a folder launcher on panel that launches a gksudo nautilus so I don't have to worry about permissions on image folders on all my drives.

---

### Post by jdpipe on 2007-02-25
Seems as though Ubuntu is getting confused as to what my 'local' files are. If I choose in preferences --> Preview --> Show thumbnails --> Always then my thumnails show up.

I am running on an external hard drive so this likely to be what's causing the confusion for Nautilus. I think I might file a bug unless anyone can suggest something I might be doing wrong.

JP

---

### Post by ^rooker on 2007-02-26
hm... but I've seen that thumbnail-feature working flawlessly on external USB drives (even cameras), so .... what kind of external drive are you using?

---

### Post by daz4126 on 2007-02-26
Just to say that this problem occured when I upgraded from Dapper to Edgy and disappeared when I tried a clean install. Not sure if that helps or not (it doesn't really identify the heart of the problem!) I think that it is something to do with the drives being recognised incorrectly - check the ids in the fstab file and see if they match with what ubuntu thinks they are.

DAZ

---

### Post by jdpipe on 2007-02-26
daz -- same applies to me. I upgraded from 5.10 to 6.06 to 6.10 and I currently have the problem.

How can I found out what it is that makes nautilus think my folder is not 'local'?

Cheers
JP

---

### Post by jdpipe on 2007-02-26
Here's my fstab. I suspect the UUIDs may be wrong, but don't know how to check.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                  <dump>  <pass>
proc            /proc           proc        defaults               0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D6-061C / ext3 defaults,errors=remount-ro 0 1
/dev/hda1       /media/hda1     ntfs        defaults               0       0
#/dev/sda3       /media/usb      vfat        umask=0000             0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=78BCCE33BCCDEC26 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto            0       0
/dev/fd0        /media/floppy0  auto        rw,user,noauto         0       0
#/dev/sdb        /media/usb0     auto        rw,user,noauto,umask=0000         0       0

---

