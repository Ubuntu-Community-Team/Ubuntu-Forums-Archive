---
title: "mounting ntfs problem"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by holiday on 2005-09-21
I can mount my xp drive but nobody but only root can read it. I know I know this is an old story, but none of the endings I've read have worked for me. I haven't read a good explanation yet, a full treatment of all the options and would very much like to see that. I could look at the code, I suppose, but there must be something a little more accessible. 

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda1       /mnt/windows    ntfs    user    0  0
# /dev/hda1       /mnt/windows ntfs nls=iso8859-1,ro,umask=0 0 0
#/dev/hda1       /mnt/windows ntfs ro,dmask=0222,fmask=0333 0 0
/dev/hda1       /mnt/windows  ntfs    auto,umask=0 0 0

I have run the script in the wiki AutomaticallyMountMSWindowsPartitions
winmac_fstab

and get this error :

error: libhal_device_get_property_type: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/block_3_1
Ignoring /dev/hda1 - already in /etc/fstab
No usable windows/mac partitions found
root@ubuntu:/home/stephen# cat /etc/fstab'

So that's it. I'm going to bed. 

I'm pretty happy with ubuntu so far. Just installed it about an hour ago and things seem to be working - except the mount command. I've had a couple of linux installations before (RH and FC) so I kinda know what should happen. 

But it's not happening.

---

### Post by aysiu on 2005-09-21
Follow these directions *exactly*.

[http://www.frankandjacq.com/ubuntuguide/5.04/#automountntfs](http://www.frankandjacq.com/ubuntuguide/5.04/#automountntfs)

Then, reboot your computer.

---

### Post by holiday on 2005-09-21
[QUOTE=aysiu]Follow these directions *exactly*.

[http://www.frankandjacq.com/ubuntuguide/5.04/#automountntfs](http://www.frankandjacq.com/ubuntuguide/5.04/#automountntfs)

Then, reboot your computer.[/QUOTE]
 Thank you. 
But why did I have to reboot? That seems very unlinux 

I tried 
$mount and $mount -a
but it did not work. It should, shouldn't it.

---

### Post by PsyberOneZero on 2005-09-21
Is it possible that the partitons were already mounted "incorrectly". I that case you would have had to do:
#umount /dev/hda1
#mount -a

Just a thought

---

