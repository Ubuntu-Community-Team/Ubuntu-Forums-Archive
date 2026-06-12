---
title: "usb stick permission problems"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-11-07
hi all.

I seem to have a major problem with the permissions of my USB stick. It just refuses to change them!

When I plug it in while in KDE it automatically mounts it and all, and the sometimes I can modify content(at least add), and sometimes not.
I added it to the /etc/fstab, which now looks like this 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /home/caligula/disk     vfat     user       0       0



I'm not sure what options I should put. And I don't really know what filesystem it is, but it works with vfat, so I guess that's alright.

I tried about ten million times to do 
```
#chown root:caligula /home/caligula/disk
#chmod 775 -v /home/caligula/disk
```

But it just REFUSES to change permissions!

I also tried opening konqueror as root and changing permissions the gui way, all I get it a progress dialog box which does not move and various access denied messages(as root!).

I'm completely jammed here, anybody can help me out? I just wanna put some music on, damn ](*,) ](*,) 

Thanks
Josh :-D

---

### Post by taurus on 2006-11-07
Try to modify the last line in /etc/fstab to look like this!

```

/dev/sda1 /home/caligula/disk vfat defaults,umask=000 0 0

```
p.s.  chmod won't work with vfat or ntfs filesystem...

---

### Post by Caligula on 2006-11-08
thanks, i had it like that before.

At the moment I went to a windows pc and did a "check drive" on it, and formatted it, now it's working for some reason, maybe it was a problem with the drive itself.. i don't know

---

### Post by Ateo on 2007-04-28
Add the following to fstab (replace sdX1 with whatever partition/drive):

1. ```
$ sudo gedit /etc/fstab
```
2. ```
/dev/sdX1	/media/disk	vfat		user,noauto,umask=000			0 0
```

Eject the disk:
```
$ sudo eject /dev/sdX1
```

Then plug the stick back in and it should still create a desktop icon and automatically launch nautilus with your usbstick contents in your face. =)

To safely eject your usbstick (just like you have to with Windows), simply right click the desktop icon and selected 'Eject'... Done.

HTH.

---

