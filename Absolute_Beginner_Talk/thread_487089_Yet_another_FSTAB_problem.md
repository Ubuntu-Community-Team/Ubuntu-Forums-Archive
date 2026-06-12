---
title: "Yet another FSTAB problem"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-06-28
I have a new machine I built, and I've got two 74G SATA drives and two 500G SATA drives.

I've been using the four drives, but am not yet certain how I want to configure things.  I decided to not automatically mount two of them, just to make it easier on the drives (not sure it would, but seemed like it might.)

This is where the problem comes in.  I can't seem to get Feisty 64-bit to honor the noauto part of the command line.

Here is my /etc/fstab file in it's entirety:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1  /  ext3  defaults,noatime,nodiratime,errors=remount-ro  0 1
/dev/sda5  none  swap  sw  0 0
/dev/hda  /media/cdrom0  udf,iso9660 user,noauto  0 0
#
# Add the other three disks
#
/dev/sdb1  /home/bob/Fastdisk  ext3  user,noauto,noatime,nodiratime,rw,dev,exec,suid  0 0
/dev/sdc1  /home/bob/Data1     ext3  user,auto,noatime,nodiratime,rw,dev,exec,suid  0 0
/dev/sdd1  /home/bob/Data2     ext3  user,noauto,noatime,nodiratime,rw,dev,exec,suid  0 0

```

Yes, I do have the mount point directories created, and they all work fine.  I have a lot of data out on sdc1, and point to it with symbolic links when I need it.

However, sdb1 and sdd1 are being auto-mounted despite my instructions above to not do so.

What's equally weird, perhaps, is that the one I called Fastdisk shows up as a mounted device on my desktop, but none of the others do.  If I go in with Nautilus and double-click on any of those mount points, the data appears instantly.  I'm thinking that I must not understand auto versus noauto.  I'm also uncertain about the "user" option.  I've seen others spell it "users".  Either way, all worked fine when I just mounted the drives using defaults, but something is really weird now.

Any thoughts appreciated.  

Thanks,
Bob

---

### Post by annda on 2007-06-28
as to user/users choice, i found this:
> 
user= when mounted the mount point is owned by the user who mounted the partition
users= when mounted the mount point is owned by the user who mounted the partition and the group users

i admit i don't understand the "noauto" anomaly but i have a stupid question: why do you include those drives in fstab if you want to mount them manually only?

---

### Post by RTrev on 2007-06-28
> **annda said:**
> as to user/users choice, i found this:


i admit i don't understand the "noauto" anomaly but i have a stupid question: why do you include those drives in fstab if you want to mount them manually only?

Hi, and thanks for the quick reply!  For some reason, your material about user versus users didn't appears when I quoted your note, but it makes sense and I appreciate the info.

As to why I put them in fstab, my confused noob thinking was that:

1) I've often tried to mount a drive only to be told I can't because it's not in fstab.

2) I thought having it in fstab would mean that all the options I chose would take effect if I then mounted the drive manually.

3) I already had them set up there, so thought a quick and temporary way to keep them from mounting would be to just add the noauto option.  When I figure out the final configuration, the drives would already be there ready to set up however I wanted.

I could easily remove them, but I thought this way it would be quick and easy to just right click on the mount point and tell it to mount the drive.. if I wanted it for some reason.

Probably a lot of flawed thinking there, eh?  :)

Thanks,
Bob

---

### Post by RTrev on 2007-06-28
Just an update on this issue.  I found why one drive showed as an icon on the desktop and the other didn't.  The drive that showed had a label set on it.  I labeled the other drive, and now it also shows up.

The core problem, though, is that the system ignores the noauto directive in fstab.  Someone on the GRC newsgroups suggested to me that it was probably an issue with gnome-volume-manager.

I did some searching on this, and it does appear that this component caused a lot of trouble for folks during Feisty development.  Perhaps it's still a bug, or perhaps there is a way to configure gnome-volume-manager to behave differently?

Thanks,
Bob

---

### Post by bodhi.zazen on 2007-06-28
I do not know the problem, but what I personally would do :

1. Remove (comment out by adding a # at the front of the line) the line in fstab.

#/dev/sdb1  /home/bob/Fastdisk  ext3  user,noauto,noatime,nodiratime,rw,dev,exec,suid  0 0

^^ Like that

2. You can then mount the partition any time you like with the mount command.

Like this :```
sudo mount /dev/sdb1  /home/bob/Fastdisk
```

unmount with umount /dev/hdb1

You can then set an alias in ~/.bashrc

alias fast="sudo mount /dev/sdb1  /home/bob/Fastdisk[/code]

Now configure sudo to allow you to run sudo mount without a password ...

And add a custom launcher to the menu call it "fast" with the command line "fast"

alias ufast="sudo umount /dev/hdb1"

...

---

