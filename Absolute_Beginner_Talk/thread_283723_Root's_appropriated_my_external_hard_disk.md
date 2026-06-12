---
title: "Root's appropriated my external hard disk"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-10-24
Hi

My western Digital external usb hard drive used to mount automatically in /media, and appear on my desktop. Also, I coould read and write to the drive.

Now, when I plug it in it doesn't mount. However, I can make it mount in /tmp, by System>Administration>disks (I've no idea why this works), only now it isn't called My Book, it's disks-conf-sda1, and it's owned by root, so I can't write to it.

I've been trying to work out how to restore my system to its former state, but without succees, but I've found I can archive my home folder on the drive (which is what  got the drive for in the first place) by using the command line and doing everything as the super user. But it is, as they say, a real kludge.

Anybody any better ideas? Perhaps I could change the ownership of the drive from root to roger (that's me) using chown, but I'm not sure if this is safe. It sounds like the sort of thing normally only done by expert system administrators - definitly not me.

Roger D

---

### Post by bodhi.zazen on 2006-10-24
> **RogerD said:**
> Anybody any better ideas? Perhaps I could change the ownership of the drive from root to roger (that's me) using chown, but I'm not sure if this is safe. It sounds like the sort of thing normally only done by expert system administrators - definitly not me.

Roger D

Although not a bad idea, I am not sure your chmod will work (permissions are set at teh time of mount).

Could you post the output of these comands:```
ls /media
groups
```As well as a copy of your fstab (/etc/fstab) ?

---

### Post by RogerD on 2006-10-24
> **bodhi.zazen said:**
> Although not a bad idea, I am not sure your chmod will work (permissions are set at teh time of mount).

Could you post the output of these comands:```
ls /media
groups
```As well as a copy of your fstab (/etc/fstab) ?

Thanks for the speedy response - I'd almost given up hope on this one.

Here's the command responses:

roger@roger-desktop:~$ ls /media
cdrom  cdrom0  hda1  My  My Book
roger@roger-desktop:~$ groups
roger adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
roger@roger-desktop:~$


And here's fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The above are all without the hard drive connected. When I connect the drive I get the following for the commands:

roger@roger-desktop:~$ ls /media
cdrom  cdrom0  hda1  My  My Book
roger@roger-desktop:~$ groups
roger adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
roger@roger-desktop:~$

And here's fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Looks as though it doesn't make any difference. Hope this all makes sense to you.



Roger D

---

### Post by bodhi.zazen on 2006-10-24
Remove My and My book from /media.

```
sudo rm -R /media/My /media/My\ Book
```And re-try your USB drive.

---

### Post by RogerD on 2006-10-24
> **bodhi.zazen said:**
> Remove My and My book from /media.

```
sudo rm -R /media/My /media/My\ Book
```And re-try your USB drive.

Brilliant! It's worked. I'll be very careful to eject My Book in future before shutting down.

Can you explain what the various terms in the command line mean?

Anyway, thanks again. It's taken me days to overcome this problem

Roger D

---

### Post by bodhi.zazen on 2006-10-24
> **RogerD said:**
> Brilliant! It's worked. I'll be very careful to eject My Book in future before shutting down.

Can you explain what the various terms in the command line mean?

Anyway, thanks again. It's taken me days to overcome this problem

Roger D

What would you like explained?

rm = remove. will not work on a directory, so add -R for recursive.

See man rm

ls = list

groups lists the groups you belong to.

The problem you had, I believe, is gnome-volume-manager (which auto mounts your partitions) uses pmount.

pmount creates a directory (mount point) in media at the time of mounting your removable device.

pmount does not like it when the directory in /media already exists. Thus removed My and My Book -> viola.

8)

---

### Post by RogerD on 2006-10-25
Thanks yet again. I had an inkling that my system was acting as  though My Book was already mounted, and I found the My file and My Book in /medai, but I didn't have the confidence to remove them. The My file was a particular puzzle. Messing about on a complex system you don't understand is, I've found, potentially very dangerous.

Roger D

---

### Post by bodhi.zazen on 2006-10-25
> **RogerD said:**
> Thanks yet again. I had an inkling that my system was acting as  though My Book was already mounted, and I found the My file and My Book in /medai, but I didn't have the confidence to remove them. The My file was a particular puzzle. Messing about on a complex system you don't understand is, I've found, potentially very dangerous.

Roger D

If everything is working, then no problems :p

FYI deleting a directory should be no big deal.

If you wanted the directory back:```
sudo mkdir /media/My /media/My\ Book
```

These directories are auto-generated by gnome-volume-manager as a part of the automount.

---

