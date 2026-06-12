---
title: "Unable to unmount."
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by El_Boti on 2005-11-03
When i try to unmount my windows partition i recieve this message. 
(I right-clicked the Desktop icon and selected Unmount in the menu).

Unable to unmount the selected volume.
umount: only root can unmount /dev/hda1 from /media/Windows

Am I doing something wrong?? 

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                /proc                  proc    defaults        0       0
/dev/sda1       /                         ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none                  swap    sw              0       0
/dev/hdc         /media/cdrom0  udf,iso9660 user,noauto     0       0
/dev/hdd         /media/cdrom1  udf,iso9660 user,noauto     0       0
/dev/fd0          /media/floppy0   auto    rw,user,noauto  0       0
/dev/hda1	/media/Windows  ntfs ro,auto,uid=1000,gid=1000 0 0

---

### Post by ltmon on 2005-11-03
Specify "user" as an option for your windows partition:

i.e.:

/dev/hda1 /media/Windows ntfs ro,user,auto,uid=1000,gid=1000 0 0

That should allow an unpriviledged user to mount/unmount.

Otherwise you can open a terminal and:

> sudo umount /media/Windows

L.

---

### Post by El_Boti on 2005-11-03
[QUOTE=ltmon]Specify "user" as an option for your windows partition:

i.e.:

/dev/hda1 /media/Windows ntfs ro,user,auto,uid=1000,gid=1000 0 0

[/QUOTE]

Tried this but sadly, did not work. 

Thanks, anyway. Any other idea is welcome.

---

### Post by kvidell on 2005-11-03
[QUOTE=El_Boti]Tried this but sadly, did not work. 

Thanks, anyway. Any other idea is welcome.[/QUOTE]
Does unmounting it as root work? From a terminal...```
sudo umount /media/Windows
```What does this give you?
- Kev

---

### Post by El_Boti on 2005-11-03
Yes this does unmount the drive,

sudo umount /media/Windows

But why i cannot unmout it from the cascade menu??   :confused:

---

### Post by kvidell on 2005-11-03
[QUOTE=El_Boti]Yes this does unmount the drive,

sudo umount /media/Windows

But why i cannot unmout it from the cascade menu??   :confused:[/QUOTE]
Perhaps now, once it's remounted, it will allow you to.

The problem before was that it was mounted without user permissions, and while you added them, it was still going by the "old" mount's rules.

If you try again, mounting it with the new permission option set in fstab, then try to umount it from the context/cascade menu, it _may_ work. I'm not sure though, never really had a box with two drives mounted in such a fasion before.
- Kev

---

### Post by El_Boti on 2005-11-03
[QUOTE=kvidell]Perhaps now, once it's remounted, it will allow you to.

The problem before was that it was mounted without user permissions, and while you added them, it was still going by the "old" mount's rules.

If you try again, mounting it with the new permission option set in fstab, then try to umount it from the context/cascade menu, it _may_ work. I'm not sure though, never really had a box with two drives mounted in such a fasion before.
- Kev[/QUOTE]

Did not work.

Kev, would you please post your fstab please??

---

### Post by kvidell on 2005-11-03
[QUOTE=El_Boti]Nope it did not work.

Kev, would you please post your fstab please??[/QUOTE]
Mine isn't going to do you any good... This is my laptop, it only has one drive...
And my systems that do have multiple drives never get unmounted because they're doing something system critical...

Like... my home directories...

But, if you insist:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```It's just the default fstab that comes with Ubuntu... Nothing fancy.

I don't know what good this'll do ya, but more power to you if it in some way helps :-D

---

### Post by El_Boti on 2005-11-03
Ok, I tought that you had a ntfs hdd mounted like what I am trying to do. But thanks.

Anyways, the problem should be in the privileges but i dont know where.

---

### Post by El_Boti on 2005-11-03
Could this be a bug ?

---

### Post by ltmon on 2005-11-03
[QUOTE=El_Boti]Could this be a bug ?[/QUOTE]

I really thought my suggestion above should work... sorry I can't test is for you though as I don't have a windows drive at all.

Anyone else who has an NTFS drive mounting/unmounting as a normal user?

L.

---

### Post by Mustard on 2005-11-03
El_Boti,

Might I suggest that you use the automatic script at this wiki page to automatically mount your windows drives and it will also make the correct entries in your /etc/fstab file. [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions")

I would also suggest that for some 'real-time' assistance with this, you might benefit from using the IRC help channel at irc.freenode.net on channel #ubuntu.  The x-chat irc client is installed by default and can be found in your Applications>>Internet menu.  It is set up to join the ubuntu servers by default.

---

### Post by El_Boti on 2005-11-03
Thanks Mustard, I will try the script, if it does not work I will try the IRC channel . As soon as I find the solution I will update.


:KS

---

